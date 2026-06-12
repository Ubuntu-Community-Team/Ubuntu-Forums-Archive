---
title: "Rebuilding ruined install - possible?"
date: 2009-07-16
forum: General Help
---

### Post by zcacogp on 2009-07-16
Chaps, 

OK. I tried to update the kernel on my 9.04 install, using the instructions here: 

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

... and trashed it. I don't know how, I think I followed everything correctly, but it doesn't work. 

I have tried to follow the 'Revert Settings' instructions from the command line on the trashed machine, using 'nano' as an editor, and everything does as it should apart from the removal of the kernel. It tells me that it cannot remove the second or third of the three parts as they aren't installed. (This may explain why it didn't work in the first place.) 

BUT, this leaves me with a trashed machine and a setup disk. The ultimate fall-back is to wipe the Ubuntu parts of the drive and re-install from scratch. But I don't want to do this; is it possible to reinstall using the install CD, BUT to retain all the settings, extra downloaded bits of software, updates and all that? 

<Whisper> It would be possible - indeed quite easy - in Windows, as it had a "Repair Installation" function when you put a disk in. This is what I am looking for, in Ubuntu. </Whisper>

All help appreciated, thanks. (Once I have sorted this out I'll then try and understand why the kernel update didn't work. I did it earlier on my laptop - the machine I am typing this on - and it worked like a swiss watch.)


Oli.

---

### Post by CatKiller on 2009-07-16
> **zcacogp said:**
>  <Whisper> It would be possible - indeed quite easy - in Windows, as it had a "Repair Installation" function when you put a disk in. This is what I am looking for, in Ubuntu. </Whisper>

<Whisper>On Windows, it's unlikely that you'd have installed a custom third-party kernel based on what someone on the Internet said.</Whisper>

I've only given that post a quick scan, but if you're unable to boot from your custom kernel, you should still have the old kernel installed and available through the GRUB menu.

Saying that you did some steps but not others doesn't really help us to help you unless you tell us clearly which steps you've done and which you haven't, and what error messages (if any) you're getting. There's (probably) no need to re-install, btw.

---

### Post by zcacogp on 2009-07-16
> **CatKiller said:**
> <Whisper>On Windows, it's unlikely that you'd have installed a custom third-party kernel based on what someone on the Internet said.</Whisper><Whisper>You're right, too. Look at the ruination that Ubuntu has bought upon me - and here I am, looking for solutions from someone else on the internet! :( </Whisper>

Looking back at the thread I was following, I went to Part C ("Optimal/Bleeding-Edge"), which bought about the problems. I ?have un-done the following:

- Changed the xorg.conf back to as it was before (removed the bits that were added.)
- Removed the extra two sources from /etc/apt/sources.conf
- Downgraded the packages. 

All of the above worked. I ran into problems with the following bit of code: 
```

sudo dpkg -r linux-headers-2.6.30-020630 linux-headers-2.6.30-020630-generic linux-image-2.6.30-020630-generic
```

When I did this, (from memory) it said something along the lines of "Successfully removed linux-headers-2.6.30-020630, could not remove linux-headers-2.6.30-020630-generic or linux-image-2.6.30-020630 as these were not installed"

The new kernel never appeared in the list displayed in GRUB, although there were some previous ones there. However, they all produce the same error (that's to say that the one at the top of the list - the previous default - produces the same error as the two further down the list). The error is that it appears to boot fine, the progress bar moves across the screen under the "Ubuntu" logo, but then the lower two-thirds of the screen fill with a series of coloured blocks and it appears to display some blurred menu bars, part of the way up. The screen blanks, and then the same pattern is displayed again. The best way of describing it would be to say that it looks like the screen plug has half come-out, but this is not the case. The only way out is to force a re-start (hold the power button in). 

All help welcomed, thanks. If I can avoid a complete re-build then that would be great. Do ask if I can post more information. 


Oli. 
[SIZE="1"]
P.S. Catkiller - Sunny Sarfend? Given the huge geographical area this forum covers, it's good to find another local(ish) lad. I'm in Lahndahn Tahn. [/SIZE]

---

### Post by CatKiller on 2009-07-16
> **zcacogp said:**
> [SIZE=1]P.S. Catkiller - Sunny Sarfend? Given the huge geographical area this forum covers, it's good to find another local(ish) lad. I'm in Lahndahn Tahn. [/SIZE]

Actually, I'm assured that the pronunciation is Sa&#601;fend. Higher in the throat.

For your problem... they call it "bleeding" edge for a reason.

> When I did this, (from memory) it said something along the lines of "Successfully removed linux-headers-2.6.30-020630, could not remove linux-headers-2.6.30-020630-generic or linux-image-2.6.30-020630 as these were not installed"

That is potentially why it didn't work. If you had the headers but no image there would be nothing to boot into. FWIW, the latest Jaunty kernel is 2.6.28-13, so you could use apt-get to make sure that you don't have anything (headers or image) from 2.6.30.

To clarify your symptoms; Does the progress bar fill up completely before the screen gets mangled (IE, that it's the login screen that's messed up) or does it happen before then (meaning that it could be a problem with the framebuffer)? If it's the former then the last two commands given may fix it:

```

sudo dpkg-reconfigure xorg-xserver
sudo rm /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default

```

If it's the latter then you must still have some traces of the updated kernel somewhere.

Synaptic has the option to show which repository a package came from. I suspect that aptitude must have something similar. This should show if you've still got some packages installed that still need to be purged.

---

### Post by zcacogp on 2009-07-17
CatKiller, 

I'll take your word for it on the pronunciation of 'Sa&#601;fend'. Wouldn't want to argue with a local about how to pronounce the name of his hometown! 

When the machine boots, the progress bar does get completely to the end - yes. It produces the messed-up screen when it should produce the login screen. 

I tried the two commands you gave me, but the result from the first one was interesting. When I put in ```
sudo dpkg-reconfigure xorg-xserver
```it came back with 

```
Package 'xorg-xserver' is not installed and no info is available. 
Use dpkg --info (= dpkg-deb --info) to examine archive files, and dpkg --contents (=dpkg-deb --contents) to list their contents. 
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed

```

I am guessing this is significant - non? 


Oli.

---

### Post by zcacogp on 2009-07-17
CatKiller, 

OK, slightly more progress. 

I *think* you may have meant to type xserver-xorg in your post, rather than xorg-xserver. If I do this, I get a number of screens which take me through a configuration process. This involves choosing whether to use a kernel framebuffer, and various keyboard configurations. 

I'm assuming that the kernel framebuffer is the relevant one, but having tried both settings, neither work. It still produces the messed-up screen instead of the login one. 

Also, when I boot the machine I go into "Recovery Mode". This displays a "Recovery Menu", one of the options on which is "dpkg - Repair broken packages". If I select this option, it says "Failed to fetch XYZ, could not resolve 'gb.archive.ubuntu.com'", or "Failed to fetch ABC, could not resolve 'packages.mediabuntu.org'. There are a number of these, and they run off screen too quickly for me to see them, but I think there are quite a few of them. 

It then tells me "The following packages will be upgraded:" and lists 12 or so packages, including libglu1-mesa, libpulse-browse0, libpulse-mainloop-glib0 and so on. It tells me "12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Need to get 1336kB of archives. After this operation, 0B of additional disk space will be used. Do you want to continue [Y/n]?"

If I say "Y", it tells me it failed to fetch a number of things (again running off screen - I don't think it fetched any of them), and says "maybe run apt-get update or try with <something>" (where <something> is off-screen.) 

If I try "Sudo apt-get update", it tells me it 'Hit' a large number of Packages (again, running off-screen) and tells me it is "Done". 

BUT none of these make any difference - the machine still won't boot. 

All suggestions welcomed. Thanks. 


Oli. 

P.S. I hope this post made sense - it may all sound a bit garbled. Do ask if I can help by explaining any of it.

---

### Post by CatKiller on 2009-07-17
> **zcacogp said:**
>  I *think* you may have meant to type xserver-xorg in your post, rather than xorg-xserver. If I do this, I get a number of screens which take me through a configuration process. This involves choosing whether to use a kernel framebuffer, and various keyboard configurations. 

Well, I didn't type it at all. It was a drag and drop from the other thread. You know how it is when you think you know what something says so you don't bother to read it. Will be more careful in the future.

> 
I'm assuming that the kernel framebuffer is the relevant one, but having tried both settings, neither work. It still produces the messed-up screen instead of the login one. Actually, probably not. I'm not entirely sure how the kernel framebuffer interacts with X, but it's normally used for putting pretty pictures in the GRUB menu and having a higher resolution for the virtual console.

> 
Also, when I boot the machine I go into "Recovery Mode". This displays a "Recovery Menu", one of the options on which is "dpkg - Repair broken packages". If I select this option, it says "Failed to fetch XYZ, could not resolve 'gb.archive.ubuntu.com'", or "Failed to fetch ABC, could not resolve 'packages.mediabuntu.org'. There are a number of these, and they run off screen too quickly for me to see them, but I think there are quite a few of them. That might be an indication of a DNS problem, or it might just be a temporary glitch with the mirror that you're using. If it goes away, it was just a temporary glitch :)

> 
It then tells me "The following packages will be upgraded:" and lists 12 or so packages, including libglu1-mesa, libpulse-browse0, libpulse-mainloop-glib0 and so on. It tells me "12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Need to get 1336kB of archives. After this operation, 0B of additional disk space will be used. Do you want to continue [Y/n]?"libglu1-mesa was one of the packages that you changed. It might be significant that there's a new version, or it might just be a run-of-the-mill update. Actually, I just checked and, although the PulseAudio updates are there, I'm not getting a libglu1-mesa update. I'm not sure exactly what it does, though.

EDIT: If you'd like a higher resolution virtual console so that the text doesn't run off the bottom of the screen, you could add a vga=0x31B (or similar) entry to your GRUB kernel line. It's probably best to do it from the GRUB menu to start with so that you know the mode works before changing menu.lst.

---

### Post by zcacogp on 2009-07-17
Catkiller, 

Thanks. 

Any suggestions on where I should go from here? 


Oli.

---

### Post by CatKiller on 2009-07-17
> **zcacogp said:**
> Any suggestions on where I should go from here?

It's quite difficult to diagnose things over the Internet, isn't it?

The two possibilities as I see it are that either you've still got some packages from the dist-upgrade that you did, meaning that you've got some rendering libraries that aren't compatible with everything else that you've still got on there, or that there's just something wrong with your X configuration.

I haven't been able to find a way yet to show on the command line which repository the packages that you've got installed have come from, which is a pain. A ```
sudo apt-get -t jaunty dist-upgrade
``` **might** change all packages to the Jaunty version, but I've never tried it.

If it's just the X configuration that's broken, then the xfix option from the recovery menu may help to set the configuration up again, although I suspect it does the same sort of thing as the dpkg-reconfigure.

Hopefully your temporary connection problem was just that, and it will work smoothly to get any updates.

BTW, if you do go for a re-install I understand that it's much easier if you have a separate /home partition for all your config files. Otherwise they all need to be backed up somewhere. There is a method (using dpkg --get-selections) to make a list of all the packages that you've installed in a text file. After a re-install you can use this list (and dpkg --set-selections) to automatically install all the packages that you had previously. I think you still need to set up users and re-do any system-wide configuration edits again, though.

Another wild stab in the dark that I've just thought of. While you're at the garbled login screen, pressing Ctrl-Alt-(NumPad minus) might set the resolution to a lower one. This lower resolution might not have the problem that the default one does. Worth a try anyway, I reckon.

---

### Post by zcacogp on 2009-07-17
Catkiller, 

It is difficult to diagnose over t'internet, I do know. Thanks for keeping going with this one. 

FWIW, I tried to follow all the instructions to install the updated kernel again (typing everything in at the command line - no copy and paste. Pain in the neck), which downloaded the three packages fine but didn't install them fine - it gave errors, and said that the build had been halted. 

However, doing this HAS put some new entries into the GRUB menu, which now looks like this: 

```
Ubuntu 9.04, kernel 2.6.30-020630-generic
Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-13-generic
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.27-11-generic
Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)

Ubuntu 9.04, memtest86+

Other operating system: 
MS XP Pro
```

However NONE of the Ubuntu kernels runs - they all give the messed-up screen problem. When I was originally playing I was doing so with the 2.6.28-13 one. What settings are common across all of these, as this would seem to be the problem? 

Neither dpkg or xfix made any difference - still same problem. 
```

sudo apt-get -t jaunty dist-upgrade
```ran, but told me that "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." So no progress. 

Ctrl-Alt-NumpadMinus didn't do anything either. 

Thanks for the suggestions about how to rebuild. Looks like this is the route I will be going at the current rate ... 


Oli.

---

### Post by CatKiller on 2009-07-17
> **zcacogp said:**
> downloaded the three packages fine but didn't install them fine - it gave errors, and said that the build had been halted.

What were the errors? (roughly)

Another thing I possibly could have mentioned before; X's log is stored at /var/log/Xorg.0.log. That might give some clues as to what the problem might be with the display when X starts.

---

### Post by zcacogp on 2009-07-17
Catkiller, 

I've re-run them, and it says: 
```

* fglrx (8.620)
fglrx (8.620): Installing Module. 
......(bad exit status: 7) 
 Build failed. Installation skipped. 
```

The installation of the new kernels produced a lot of text, and again I've got the going-off-the-screen problem, but it looks like this could be something to do with /etc/kernel/postinst.d/nvidia-common. 

I can open the X Log file you mentioned, thanks. Snag is that it is quite long and I don't know what I am looking for. A search for 'failed' using nano gives two instances: 

```
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
```

and
```

(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
```

I don't know if this is of any help. 


Oli.

---

### Post by CatKiller on 2009-07-17
I'm confused. What graphics card have you got?

> **zcacogp said:**
>  I've re-run them, and it says: 
```

* fglrx (8.620)
fglrx (8.620): Installing Module. 
......(bad exit status: 7) 
 Build failed. Installation skipped. 
```


OK. So it's tried to configure the proprietary Ati driver, which has failed. If you've got an Ati card and you wanted to use the proprietary driver that could be a problem.

>  I can open the X Log file you mentioned, thanks. Snag is that it is quite long and I don't know what I am looking for.

Yeah, that sucks a bit. Especially without being able to copy-and-paste the contents back here.

(EE) means error, btw, and (WW) means warning, in case that helps pinpoint any problems.

One possibility is to try ```
sudo nano /etc/X11/xorg.conf
``` to put a line that says ```
        Driver          "vesa"
```in the Device section, in case the (bog-standard) VESA driver has more luck than the open-source Radeon driver. I believe that the VESA driver doesn't even try to load the advanced things like [DRI]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure").

---

### Post by zcacogp on 2009-07-17
Catkiller, 

The graphics card is the built-in one on the motherboard. It's an 'ATI Radeon HD 330 Graphics', if that means anything to you. 

I've tried the "Vesa" line in the xorg.conf file; no game. Same as before. 

Looks like a rebuild is the best option, unless someone else has some other ideas. 

Thanks again for your help with this Catkiller. It's appreciated. 


Oli.

---

### Post by CatKiller on 2009-07-17
One last random thing to try. When you get to the garbled login screen, can you log in blind?

---

### Post by zcacogp on 2009-07-17
> **CatKiller said:**
> One last random thing to try. When you get to the garbled login screen, can you log in blind?Good idea. 

Didn't work. 

Just put the Ubuntu desk in the CD drive ... thanks again for your help. 


Oli.

---

### Post by CatKiller on 2009-07-17
Ah well. Sorry we couldn't make it work again. Good luck for next time.

---

### Post by zcacogp on 2009-07-17
Catkiller, 

Thanks again for your help. 


Oli.

---

### Post by zcacogp on 2009-07-17
Well, one to make you go "Gggrrrrr" ... I have rebuilt, and re-tried the kernel upgrade, as per the instructions (on a bare-bones build, no other stuff installed.) 

Guess what? It worked fine. First time. And I am writing this message on it ... 

Sick? I am. Not sure what went wrong first time 'round. 

Thanks again for your help. 

>OffToCompleteTheRebuild<


Oli.

---

### Post by CatKiller on 2009-07-17
> **zcacogp said:**
> It worked fine. First time. And I am writing this message on it ... 

That's... good... I guess? :)

Glad you're back up and running again.

---

### Post by zcacogp on 2009-07-19
Catkiller, 

Ha! Well, here's a bit more on the story (if you are disinterested then I'm sorry!) 

I re-built. 90% of the way there, I discovered that Compiz wouldn't work because I was using the standard screen driver. So I updated it (which I had done on the previous install), and re-booted ... and guess what, it produced *exactly* the same messed-up screen again! 

So. Pretty-much definitive proof. The ATI driver that was installed disagrees with the 2.6.30 kernel. The question is whether there is any way I can remove the new kernel OR downgrade the screen driver without rebuilding it all ***again***. 

I'll have a gander on the upgrading-kernel thread to see whether this has been reported and how to get out of it, and will post another thread on here if I come unstuck. (Unless you happen to know the answer off the top of your head?) 

Thanks again for your help. This new happening is kind-of encouraging as it means there is a definite diagnosis of what went wrong. 


Oli.

---

### Post by CatKiller on 2009-07-19
I'm afraid I've never used the fglrx driver, so I really don't know what else it needs to work properly. That's the problem with proprietary software; any change requires the blessing of whoever controls it.

> **zcacogp said:**
> This new happening is kind-of encouraging as it means there is a definite diagnosis of what went wrong.

Indeed. With a firm diagnosis, you should file a bug report, and hopefully there will be a fix for you. If not now, then in the future.

---

