---
title: "KVM switch with 10.04"
date: 2010-08-24
forum: General Help
---

### Post by garyed on 2010-08-24
Is anyone using a kvm switch without any problems?
I've been dealing with this for 3 years now & still haven't solved it.
I've got two different kvm switches & they both have the same problem.
Ubuntu no matter what version will only work correctly on the first port.
The two switches I have are a 2- port trend-net & a 4 port Alluratek, they both do just monitor,keyboard & ps2 mouse. The problem is only with the monitor. The resolution is stuck at 800/600 or else it only covers part of the screen. After messing with xorg forever in Hardy I finally got it working but upgrading to 10.04 I just give up. Windows never has a problem detecting my monitor with the kvm switches but Ubuntu does. Anyone have any suggestions?

---

### Post by held7over on 2010-08-24
I don't know if this applies to what you are talking about, or not. I have been running using a Belkin KVM switch that accesses two computers running Ubuntu since 8.04 and am now up to running 10.04.

It can be kind of flaky, sometimes. For instance, the most common problem is if you boot up on one machine, and are viewing something on another machine, the machine booting up, if it reaches the login BEFORE you switch over to it, the resolution will be _WAY TOO LOW!_ 

However, if you hit the power switch to boot the computer, and then wait a bit so that you are at least half way to the login screen in the bootup process and then switch to that computer, the resolution will be where you have it set at....and everything will be fine. For me, if I already have another computer running, if I jump too soon in the boot up process to that computer, the KVM switch will wait a bit, and then automatically switch back to the first computer, and before I can get it to switch back the login screen will already be there and be at the wrong resolution. So, it is a bit of an art...or you need to time it so you always get it right.

You can, of course, always try restarting the computer and hope the KVM switch doesn't cause you to jump away while it is doing the restart.

Once in a great while, when booting up, whether or not another computer is already up and running, the KVM switch will start jumping every 5 seconds or so, back and forth between the two computers all by itself, whether or not the second computer is running or not. In that case, you must shutdown the computer(s) and start over. This is rare.

Now. All that said, I have seen on the Internet a FIX of some kind, that eliminates these problems I just described. This has something to do, I think, with wiring two pins together on the computer side on each of the computers you are using the KVM switch on. I think I also saw another fix by simply removing the other resolution options in the Operating System files.

If you google (KVM SWITCH RESOLUTION) for it, you will probably find it. 

Since I only had to be viewing the booting computer to fix my problem, I decided not to risk wiring stuff together. But I have ran into that wiring fix several times, by different people discussing this problem and other associated problems.

Hope this helps.

---

### Post by garyed on 2010-08-24
Thanks,

I'll take a look at some of those things.
It's been kind of frustrating.
It wouldn't be so bad if it wasn't that Windows behaves fine with both of my kvm switches so I've got to think the problem lies with Linux.I think Windows doesn't care what monitor you have hooked up it just goes by your driver settings where Ubuntu actually looks for your monitor & adjusts to what it sees.

---

### Post by X5-655 on 2010-08-24
This could be solved if they made a smart KVM switch that read the EDID data from the monitor, and saved it to memory for all machines attached.

---

### Post by garyed on 2010-08-25
Well so far nothing has worked.
I even tried to use my xorg.conf file from my Hardy version that works fine on the same computer but it doesn't work right on 10.04. The resolution seems O.K. but a good part of the screen is cut off on the top & sides where I can't even access the menus. I think I need to find the setting for the actual monitor size or something to make it work. I have a standard 4:3 19" monitor if anyone knows what the settings should be.

---

### Post by garyed on 2010-08-25
A little update:

By resetting the monitor the screen fills up O.K. now but i realized that my resolution is stuck at 1024x768 with no other options.
I also notice there ia a file /etc/X11/xorg.conf.failsafe that wasn't there before. If I could find the right place to put my screen resolution in that file I bet it would work.

---

### Post by heviiguy on 2010-08-25
This seems typical: One goup of Users experiencing mind-numbing problems with a certain aspect of Ubuntu that some don't even blink at.

Along with hordes of others, I have terrible problems with Samba on 10.04. Yet, KVM switching poses no problem at all. I have three dual-boot boxes. Depending on which box I've got connected obvioulsy, I can easily switch between linux box-linux box or windoze box -linux box. 

I didn't even know that such an issue existed. :o

---

### Post by garyed on 2010-08-25
> **heviiguy said:**
> This seems typical: One goup of Users experiencing mind-numbing problems with a certain aspect of Ubuntu that some don't even blink at.

Along with hordes of others, I have terrible problems with Samba on 10.04. Yet, KVM switching poses no problem at all. I have three dual-boot boxes. Depending on which box I've got connected obvioulsy, I can easily switch between linux box-linux box or windoze box -linux box. 

I didn't even know that such an issue existed. :o

What KVM switch are you using?
I wish they had some sort of database for which kvm switches work with Ubuntu & which don't without some tweaking.

---

### Post by heviiguy on 2010-08-25
Darn. I was afraid that somebody was going to ask. 

After climbing under my desk, I can report that it's an Iogear USB KVM switch. I'm not sure what the model ID is but, if I were to hazard a guess, I'd say (based on a quick net search and comparing pictures to the real thing) it's a GCS632U.[]("http://www.google.com/url?url=http://www.iogear.com/product/GCS632U/&rct=j&sa=X&ei=UVJ1TPbeBcH38AbpsdzFBg&ved=0CB4QzgQoADAA&q=iogear+miniview+usb+kvm&usg=AFQjCNEXHVYEiBggHYBQKRdd-Do75_vNfw&cad=rja")

---

### Post by garyed on 2010-08-28
I was all ready to buy a third KVM switch when I came upon an older post that pointed me to this:
 [http://robert.penz.name/219/workaround-for-the-ubuntu-problem-with-kvm-switches/](http://robert.penz.name/219/workaround-for-the-ubuntu-problem-with-kvm-switches/)

It seems that this xorg.conf file allowed Ubuntu to use 128x1024 & without it would not allow anything over 1024x768.

---

### Post by heviiguy on 2010-09-07
Sorry for the delay in responding; I've only just recently returned to civilization.

If this workaround is all that it takes, then why did my KVM work without me having to do this? Seems to me that there is something else amiss here.

Notice how I wrote "did"? Since this morning I've experienced sporadic keyboard control. I'm now at the point where the keyboard is directly plugged into the laptop. Weird  :confused:

---

### Post by spelingchampeon on 2010-09-18
I posted the below text on the Linux Mint site about a month ago. No one has replied to it, which tells me either no one else has experienced this issue, or no one knows of a fix. I'm sure this has something to do with the Xorg changes made over the last couple of releases, and it is truly frustrating to say the least. Linux Mint is based on the Ubuntu OS. Thanks:

[COLOR="darkgreen"][I]Is there anyway to have the system bypass looking for the monitor (but its not headless) so I can use a KVM? I can boot it up with the monitor connected, go into the NVIDIA config, set the resolution and then save the config.. but as soon as I put the KVM back in, and reboot (next day for example), the xorg.conf is automatically overwritten to something insane. The original xorg.conf is now a backup, but I can not switch to backup (and I shouldnt have to). If I open the NVIDIA config to try and adjust it, I get the following error:
It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

to which I answer yes.. then get this:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

If I restart X, it get a runaround that does nothing. I've reinstalled the OS, and done everything I could find on this site, but no go. Already lost 8 hours of my life...[/COLOR]

LM 9.0
AMD 3200+ CPU
ASUS AV8-VM SE Motherboard
1.5gig memory
EVGA Nvidia 210 video card[/I][/COLOR]

---

