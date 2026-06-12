---
title: "Switched Nvidia card to new ATI card. Need help."
date: 2011-12-07
forum: General Help
---

### Post by DarkSim on 2011-12-07
I dual boot Ubuntu 11.04 and Windows Vista 32 bit. I have been running them without problem for a while now. Recently I upgraded my video card to a ATI HD6450 from a Nvidia 7600GS. I got it running smoothly on the Vista side but due to shortsightedness on my part I can only log into Ubuntu in text mode.

I believe I need to still uninstall Nvidia drivers before I can proceed back to a graphic desktop. How can I do this through text mode?

Thanks in advance for the help.

---

### Post by warfacegod on 2011-12-07
That depends on how you installed the nVidia drivers.

---

### Post by DarkSim on 2011-12-07
I think it was through the Restricted Drivers pull down menu.

---

### Post by oldtimer7777 on 2011-12-07
Is your driver supported:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)


Have you manually installed the radeon drivers for it? 


When I install Catalyst, I always do it myself. Here’s some short  instructions you can follow to do the same (this is for a 64-bit Ubuntu  OS, but you can change it to 32-bit to work for your installation):
 1. [Go to amd.com and download your driver]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
2. Run: sudo apt-get –purge remove fglrx*
3. Run: sudo apt-get install dh-make execstack dh-modaliases dkms lib32gcc1 libc6-i386
4. Go to the directory you [downloaded]("http://support.amd.com/us/gpudownload/Pages/index.aspx") the driver in (usually ~Downloads)
Run: sudo chmod +x ati-driver-installer-11-10-x86.x86_64.run
Run: sudo sh ati-driver-installer-11-10-x86.x86_64.run –buildpkg Ubuntu/oneiric
Here I assume you are using Ubuntu 11.10. If you’re using another version, use that version’s name, for example Ubuntu/maverick
5. Run: sudo dpkg -i *.deb
6. Run: sudo aticonfig –initial -f



> **DarkSim said:**
> I dual boot Ubuntu 11.04 and Windows Vista 32 bit. I have been running them without problem for a while now. Recently I upgraded my video card to a ATI HD6450 from a Nvidia 7600GS. I got it running smoothly on the Vista side but due to shortsightedness on my part I can only log into Ubuntu in text mode.

I believe I need to still uninstall Nvidia drivers before I can proceed back to a graphic desktop. How can I do this through text mode?

Thanks in advance for the help.

---

### Post by zcacogp on 2011-12-09
Why did you change the card? (This may be a stupid question - forgive me if it is.) 

I have just installed an NVidia card into my machine to use instead of the on-board ATI (HD3300) graphics the motherboard has. Someone suggested it as a solution to a number of very annoying problems that I have had with Ubuntu installations, and it has transformed the machine! I am told that NVidia is supported much better on Ubuntu than ATI, and am delighted by the improvement I am experiencing. 

I know it's not a lot of help for you (sorry), but you may just find that the NVidia card works better for you than the (newer) ATI one. 


Oli.

---

### Post by jim_deadlock on 2011-12-09
+1 for nvidia.

My dad runs Ubuntu and recently bought a new Dell machine with the exact same card as the OP (ATI Radeon HD6450) and I went through hell with that thing, it was awful. Anyway, to cut a very long story short, there seems to be no way to get the regular drivers to work, it was necessary for me to download the proprietary driver from the AMD website:

[AMD Radeon HD6450 driver for Desktop (64bit)]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Before installing that, you must first purge all the other drivers (fglrx etc) like so:

[Purge graphics drivers]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

... then run that install file. Oh, and another tip which took me many more hours to finally work out: when you run it, you'll get a choice of what to do and the first option is [1] which usually means it's the default and you just hit enter - not in this case! You must specifically type "1" (I swear I could happily strangle the person who created that little masterpiece).

---

### Post by warfacegod on 2011-12-09
Agreed. nVidia writes the best video drivers for Linux. ATi is getting better but still don't compare. Intel, however, ...not so much.

---

### Post by larrypg on 2011-12-09
Hello all,

Granted I am using a different card, AMD 6770, but the additional drivers work well for me.

---

### Post by Dlambert on 2011-12-09
> **oldtimer7777 said:**
> Is your driver supported:
 
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)
 
 
Have you manually installed the radeon drivers for it? 
 
 
When I install Catalyst, I always do it myself. Here’s some short instructions you can follow to do the same (this is for a 64-bit Ubuntu OS, but you can change it to 32-bit to work for your installation):
1. [Go to amd.com and download your driver]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
2. Run: sudo apt-get –purge remove fglrx*
3. Run: sudo apt-get install dh-make execstack dh-modaliases dkms lib32gcc1 libc6-i386
4. Go to the directory you [downloaded]("http://support.amd.com/us/gpudownload/Pages/index.aspx") the driver in (usually ~Downloads)
Run: sudo chmod +x ati-driver-installer-11-10-x86.x86_64.run
Run: sudo sh ati-driver-installer-11-10-x86.x86_64.run –buildpkg Ubuntu/oneiric
Here I assume you are using Ubuntu 11.10. If you’re using another version, use that version’s name, for example Ubuntu/maverick
5. Run: sudo dpkg -i *.deb
6. Run: sudo aticonfig –initial -f
 
 
Thank you, I bought a Radeon HD 6950 (unlocked to a 6970) and was wondering how to do this. Coming from a Nvidia GTS 450.

---

### Post by oldtimer7777 on 2011-12-09
> **Dlambert said:**
> Thank you, I bought a Radeon HD 6950 (unlocked to a 6970) and was wondering how to do this. Coming from a Nvidia GTS 450.

Everyone should avoid ATI like the plague until we can get comparable support like we do with other 3rd party video drivers, i.e. intel, and nvidia.. etc etc.  I think a good percentage of problems that user post in the general forums are due to the fact they are using ATI video drivers over the last couple of years of being here trying to help them, IMHO.  Anything is better than ATI, even the lousy on-board graphics if nothing else. If someone bought an ATI to swap out a nvidia card, they just don't know what they are doing.

---

### Post by QIII on 2011-12-09
Oh, the old "ATI sucks!" stuff again.  Sigh.

I've always used AMD/ATI and have had virtually no problems.  Even back in the bad old days when ATI really did suck.  The old saw about "bad ATI drivers" is tiresome.

Just some history, folks.

ATI, before it was purchased by AMD, did indeed seem to lack any interest in writing good drivers.  But AMD bought them (well, it was finalized) in 2008.  Since then, AMD has made a great commitment to Linux.  They are a member of the Linux Foundation.  NVIDIA?  Well...

Just as with anything else, what you are familiar with seems "right" somehow and what you are not familiar with seems "wrong" somehow.  You expect the things with which you are not familiar to behave as those with which you are familiar.  That's the problem.

There has been some advice given, so I won't go over traveled ground.  But for the future I would recommend the following course of action to the OP:  Particularly with graphics cards, if you intend to change OEMs, first remove all drivers for the current brand.  Shut down.  Install the new card.  Reboot.  That avoids having OEM X's driver on board with OEM Y's hardware.

Ubuntu (and all the other distros I use) will recognize the new hardware and start with at least an open source driver to get you going.

The one thing to remember with AMD/ATI:  After installing the driver, make sure to do 

```

aticonfig --initial

```

in the konsole/terminal before shutting down.

Both NVIDIA and AMD/ATI produce great products and have excellent drivers.  What you use is a matter of personal taste and your own needs.

(I have one machine running 24/7 with four old 5870s doing Folding@Home...)

---

### Post by Dlambert on 2011-12-10
I currently believe the Price per performance is better with AMD, (in windows at least) So that is why I bought what I did. And I love how AMD is almost constantly improving their Linux support nowadays.

---

### Post by jim_deadlock on 2011-12-10
**@QIII** - I agree with your statement that ATI have good products and good drivers - my dad's video works nicely now that it's installed, I've got the compiz cube running etc. However, you're totally missing the point which is that in many cases these (perfectly good) drivers are very difficult to install for the average user. I consider myself not a total noob, I've been using Ubuntu exclusively for about 3 years now and I'm comfortable with the terminal etc. but I found it a nightmare to install the thing and the OP has the same problem.

For me the nightmare started as soon as I installed Ubuntu on a fresh new computer, I ran updates then ran jockey just as I've done many times before. Then I rebooted and there was no GUI, all I could do was boot into recovery and get a shell prompt. The OP is facing a similar situation. For the average user this is a catastrophic problem. In my case it took me many hours of research, trial and error, system reinstalls etc etc before I managed to get it working. For the first few hours I wasn't even aware that the problem was my video driver :(

You say: "make sure to do aticonfig --initial" but who on earth would know that unless they have advanced knowledge? The OP started off with an nvidia card which would have worked for him straight out of the box. He would naturally expect the same thing to happen when he plugged in a new, modern ATI card. If this was not the case then he would not have bought the ATI card in the first place I'm sure.

Sorry if this sounds like a rant, it's not meant to be, I'm just trying to explain the frustration associated with ATI drivers for the average user.

---

### Post by DarkSim on 2011-12-16
> **zcacogp said:**
> Why did you change the card? (This may be a stupid question - forgive me if it is.) 

I have just installed an NVidia card into my machine to use instead of the on-board ATI (HD3300) graphics the motherboard has. Someone suggested it as a solution to a number of very annoying problems that I have had with Ubuntu installations, and it has transformed the machine! I am told that NVidia is supported much better on Ubuntu than ATI, and am delighted by the improvement I am experiencing. 

I know it's not a lot of help for you (sorry), but you may just find that the NVidia card works better for you than the (newer) ATI one. 


Oli.

Oh I know that nvidia works better on Ubuntu. Ran the 7600gs for years with no problems and a fx5700 with minimal problems before that.

The reason I got the ATI card was had to do some upgrades to be able to play Skyrim and I have a limited budget. The card was only 30 bucks new so I figured why not.

Thank you for all the suggestions so far. I have not had the chance yet to run through all of them. I'm sure this is one of those pebkac errors and once I get it sorted will have limited problems.

---

