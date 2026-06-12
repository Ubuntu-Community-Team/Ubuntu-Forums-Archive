---
title: "downloaded wine, now can't boot Karmic"
date: 2009-11-20
forum: General Help
---

### Post by dsimpson on 2009-11-20
I downloaded wine from the repositories and when I went to open a windows  crossword program, I received a message box which said something to the effect of "web setup" and it just stayed there and didn't complete the action. I was unable to close the window, unable to restart so I rebooted. Upon reboot the installer "grub" would not allow the sign in box to come up. I just got a terminal screen which was flashing with my signin name but I couldn't sign in because of the flashing. I went through safe mode and tried to log in, tried to repair etc, but it only took me to a terminal screen, and I am unable to log on or boot KK. This never happened until I tried using "wine" and I would like to know how to get this resolved.

---

### Post by lavinog on 2009-11-20
> **dsimpson said:**
> I downloaded wine from the repositories and when I went to open a windows  crossword program, I received a message box which said something to the effect of "web setup" and it just stayed there and didn't complete the action. I was unable to close the window, unable to restart so I rebooted. Upon reboot the installer "grub" would not allow the sign in box to come up. I just got a terminal screen which was flashing with my signin name but I couldn't sign in because of the flashing. I went through safe mode and tried to log in, tried to repair etc, but it only took me to a terminal screen, and I am unable to log on or boot KK. This never happened until I tried using "wine" and I would like to know how to get this resolved.

How did you reboot?  Did you use the reset switch?...if so the delay on the next startup was probably due to fsck doing some file system checks...I don't know if the new grub splash gives any feedback for this anymore.

how long did you wait during boot?

you might want to just reinstall...You could fix the boot issue, but there might be another issue.

---

### Post by dsimpson on 2009-11-20
Thank you for your reply, I first tried to remove or close the message box, I couldn't close it and it wasn't responding in any way. I probably had it on there about 10 minutes before I rebooted by clicking on the quit icon and pressing restart. Upon restart the problems began. Prior to this I was able to get the grub splash but not since.
By reinstalling do you mean booting and doing a new install from my livecd? I would then lose all settings and saved documents, that is why I was trying to remedy this rather than a new install. Is this the only solution? If so and I don't get any further advice than I guess that will have to be my only option, right?

---

### Post by P4man on 2009-11-20
Is this a wubi install?
If it is, your hard reset may have corrupted the host (windows) file system. Just try booting windows and do a chkdsk.

If its a normal install, can you boot in to recovery mode?

---

### Post by dsimpson on 2009-11-20
No Windows, No Wubi, this is a normal install, I have had Karmic on since the day of its release and experienced limited problems (with flash) but nothing like this. I was going to use wine to do a crossword puzzle (.exe file) and tried to open that. I tried safe mode (recovery?), regular boot, but cannot even get to the login screen. I can only get to the terminal screen which says login name, but cannot enter anything so am unable to boot.

---

### Post by P4man on 2009-11-20
Its called recovery mode afaik, are we talking about the same thing? In the grub menu the second option:
[[IMG]http://i3.photobucket.com/albums/y71/Cocasoca/th_grub2.jpg[/IMG]](http://media.photobucket.com/image/grub2 karmic/Cocasoca/grub2.jpg?o=1)

That shouldnt prompt you for a login it should give you a menu like this:

[IMG]http://1.bp.blogspot.com/_LKra8AUL9bY/SRleYPWhWfI/AAAAAAAAALY/MetRjP9OxqU/s400/20081111149.jpg[/IMG]

 Does it?

---

### Post by dsimpson on 2009-11-20
Oh ok. I went that route alright, tried resume normal boot, repair broken packages, file system check, but not the one you point out, try to fix x, I don't know if I missed that or it wasn't there. I will reboot now and try it if it is there. I have to close out this HD, boot into Ubuntu on my 2nd HD. I am posting this on LinuxMint on another HD on the same computer. Be back soon.

---

### Post by P4man on 2009-11-20
its just a screenshot I grabbed somehwere,  I wasnt telling you to pick "xfix" though it wont hurt to try. The one im more interested in is "root", and if that gives you a root shell or not, and if you can enter commands there.

---

### Post by dsimpson on 2009-11-20
I don't know if there is a root command but I did go into "safe mode" which brought me to a terminal or shell screen, no box around the screen like in terminal, just a screen with login, password etc. I can enter commands there but don't know what to do to reset or make changes to the OS. 
I didn't have the Xfix choice anyway so that option was out.

---

### Post by P4man on 2009-11-20
I dont know. Its hard to guess whats going on when you dont give exact explanations of whats happening. you could try 
```

startx
```

in a root prompt and see if that gives you a gui for root (be careful what you do there!). If it fails give us the error message. But its weird if your grub menu uses different names and the recovery console doesnt have an xfix option. Is this a fresh Karmic install or did you upgrade from 9.04?

---

### Post by lavinog on 2009-11-20
If you have a spare drive, you should be able to use the live cd to access your drive, and backup your documents, and such...this way you could to the reinstall.
I wonder if you rebooted during an update...did you have updates set to install in the background?

---

### Post by dsimpson on 2009-11-20
This was a fresh install, although I did install (also) an upgraded version of Nvidea driver earlier and maybe on the reboot it might have been the cause for my problem. I have been trying to go through my memory and try to isolate the possible causes, although I didn't have any problems prior. I will give your suggestion a try. The reason for my reboot though was the web setup box that was on my desktop that I was unable to close so naturally I first suspected that as the cause. Thank you for your help!

---

### Post by lavinog on 2009-11-20
Proprietary drivers can do that.
by "upgraded" did you mean a newer driver than what karmic offers?
What version was that?

---

### Post by dsimpson on 2009-11-21
No, the upgrade was downloaded through the software center or whatever it is known as now. I downloaded for installation the NVIDEA-Linux-X86-1.0-7185, which was the remommended driver for the NV10-GL NVIDEA graphics card. This is equivalent to the GeForce256 according to NVIDEA  customer care. This driver would be termed a "legacy" driver, and the downloaded driver should have been the replacement. I used the Ubuntu install and didn't manually do the upgrade.

---

### Post by lavinog on 2009-11-21
> **dsimpson said:**
> No, the upgrade was downloaded through the software center or whatever it is known as now. I downloaded for installation the NVIDEA-Linux-X86-1.0-7185, which was the remommended driver for the NV10-GL NVIDEA graphics card. This is equivalent to the GeForce256 according to NVIDEA  customer care. This driver would be termed a "legacy" driver, and the downloaded driver should have been the replacement. I used the Ubuntu install and didn't manually do the upgrade.

did you download that through the software center, or from nvidia's website?

according to nvidia ([here](http://www.nvidia.com/object/linux_display_ia32_1.0-7185.html)) that version was released April 20, 1007.  I doubt that driver is compatible with the current Xserver and kernel.
[This page](http://www.nvidia.com/object/linux_display_ia32_71.86.11.html) says that NVIDIA-Linux-x86-71.86.11 is the latest driver for the legacy GeForce256.

Did you use the hardware drivers application to install the driver (see attached image)?

---

### Post by dsimpson on 2009-11-22
Hi, I downloaded via software center, not through the NVIDIA site. No, I didn't use the hardware driver installation tool, I didn't know all the steps that I needed to do, so missed that step. Thanks for the heads up on the proper driver, I just went off of what I was given from the NVIDIA customer care email response.

---

