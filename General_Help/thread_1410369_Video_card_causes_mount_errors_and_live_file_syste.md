---
title: "Video card causes mount errors and live file system not found"
date: 2010-02-18
forum: General Help
---

### Post by popcultvintage on 2010-02-18
I'm of course new to ubuntu and I have done tons of research for the past two weeks to trouble shoot my problem.  I will try to provide every bit of info I can remember.

i have installed ubuntu successfully now, but I am still having the same issue from the beginning.  So let me start at the beginning.

I have a PC that has a intel D945GTP motherboard that I think has a P4 3.2 chip in it. I was running windows on it and using a Nvidia mx4000 graphics card to server s-video to my lcd.  

I use this computer for a music server and to watch abc.com and things like that on it.  so the video card is a big part of the use.

I decided I wanted a more Stable operating system so i researched and found ubunutu.


When i first went to install, I would get these errors after the white ubuntu logo.  Sometimes i would hit escape.

It filled the screen with mounting errors such as:
warning:  check bios for corruption.
mount: a long line of stuff then (failed to mount cd rom.  Invalid argument)
then it would spit out:
no live file system found

busy box stuff and then a command line

(initramfs)


so i did some research and decided that it was the video card causing the trouble.

I took it out and installed ubuntu successfully with a monitor from the onboard video.

I then rebooted a couple of times successfully.

I then wanted to get this Nvidia Mx4000 working.  So i did more research and found a couple methods.  One...envy:

I downloaded Envy to install the driver.  After i downloaded, i shut down and  I put the video card back in, booted and i got this: 

these errors were different then when i tried to install the OS the first time.
a series of mounting errors but this is what i could see:

mount: mounting /dev/disk/by-uuid/ad500553-ed1d-4de4-98bb-83e89db645e9 on /root failed: Invalid arument
Mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting / sys (same as above)
mount: mounting /proc (same as above)
Target filesystem doesnt have /sbin/init.
No init found. try passing init=bootarg

busy box (ubuntu 1:1.13.3-1ubunutu7) built in shell
and
(initramfs)

___


so then i started thinking and went into bios.  the video was set to auto.  I set it to:
Ext PCI and got the same error as above.

then i set bios video to INT and the onboard video worked again.  
the onboard vid did not work any other time.

Now..I went to Envy and envy found the card, recommended a driver and I accepted it.  Envy of course crashed in the middle of downloading the driver. then the gui wouldnt work.  so i went to the text version and it still didnt work.

threw envy out and uninstalled it.

then i went the nvidia official route.  got the driver it recommended from the web site.  Followed the linux read-me exactly.  
The installer worked the x=server config seemed to work and all said successful.

i then rebooted and everything booted with onboard video with monitor and tried to switch to the card.  it did not work.  the nvidia software showed up in the menu and everything.  but just gave me options to check and a big window with nothing in it.

So then i went back into bios, tried Auto for Video setting and got this again:
mount: mounting /dev/disk/by-uuid/ad500553-ed1d-4de4-98bb-83e89db645e9 on /root failed: Invalid arument
Mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting / sys (same as above)
mount: mounting /proc (same as above)
Target filesystem doesnt have /sbin/init.
No init found. try passing init=bootarg

busy box (ubuntu 1:1.13.3-1ubunutu7) built in shell
and
(initramfs)

When i try to do any sudo commands or anything like chroot, it just gives me errors at this commandline. like cant find and something like
/bin/sh: sudo: not found

or cannot execute /bin/sh: nosuch file or directory


I tried the ext pci again in bios and again the same thing.

I'm new, so i really dont understand these errrors.  any Help would be greatly appreciated!!

---

### Post by capsitan on 2010-11-07
This same thing happens to me as well. I can boot using internal VGA, but not with PCI. The weird thing is that I can actually use my PCI card if i boot with VGA as first priority in BIOS. I cannot even use any adapter when i choose PCI as boot priority. Can anyone help us???

---

