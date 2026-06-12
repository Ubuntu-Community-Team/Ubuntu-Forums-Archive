---
title: "Installing 10.04-RC with Silicon Image SATA 3114 controller"
date: 2010-04-28
forum: General Help
---

### Post by RayJohns on 2010-04-28
I've installed Ubuntu a few times with no problems.  However, tonight I tried to install it on an AMD machine with an SATA 3114 Silicon Image controller.  

The install seems to go okay, but when it goes to shut down at the very end, I see a bunch of error messages about being unable to release the file system or something.  Then upon the first boot, it fails and ends up a prompt window.  Basically it says it can't locate the boot image.  If you try something like "ls /boot" there is no boot directory.

In searching, it appears this has to do with no support for the sata_sil module (?).  Is this a case where that module (to support the 3114 controller) needs to be compiled into the boot image?  If so, how can I do that?

Does anyone have any information and/or can someone point me the right direction as far as resolving this issue so that I'm able to boot off the Sata drive.

I just asked in the IRC channel and I get the impression that compiling in supprot for my Sata driver into the kernel and boot image isn't really supported?  Someone else suggested adding it in as a module using "initramfs".  

Anyone have any experience in this area?  As near as I can figure, the stock boot image doesn't have support for my sata controller, but I'm not 100% sure exactly what the issue is here.  

Any advice?

Thanks!

Ray

---

### Post by RayJohns on 2010-04-29
I installed an IDE drive and turned off the SATA hard drives.  Still getting the error.  I no longer believe it's related to the sata_sil driver, since that appears in dmesg and because Ubuntu can access the drive fine during install, etc.  

In check on google, I found some posts that suggest the error I'm seeing has something to do with a bad CD burn perhaps.  I'm gonna try burning to a DVD and see if that makes any difference.  The error I'm getting is this... after the install from the CD is almost done, it says click to reboot.  Then I get a black screen which is shutting everything down.  It says All processes ended within 3 seconds... then a few more lines and then it says this:

* casper is resyncing snapshots and caching reboot files...

then I get a bunch of error messages about this:

end_request: I/O error on device sr0, sector XXXX
Buffer I/O error on device sr0, logical block XXXX

That goes on and repeats, along with some other messages.  Then I see:

error: unexpectedly disconnected from boot status daemon

then when I go to boot up, it fails to boot and drops me into a shell window.  

Any ideas?

Ray

---

### Post by RayJohns on 2010-04-29
No luck.  I tried installing from within the "try it from the CD".  That almost worked, but still strange errors.

I think the problem relates to something on the motherboard maybe.  Or perhaps how the Sata raid functions.  It seems like the boot loader is looking for the sata controller when it shouldn't.  I'm not really sure what the problem is, but I know with Windows XP I have to load a special driver for the SATA at boot/install time.  

I did check the makers of the sata controller and it appears the more recent kernels do include support for it.  The fact that Ubuntu boots fine off the CD, but then goes nuts when booting off the hard drive suggest that the issue is related in some form to the hard drives.  However, even when I kill power to the sata drives and only show an IDE drive, I still get the same error (however, the sata is on the motherboard and I don't think I can disable it).

Anyway, Ubuntu is running great on my laptop.  The desktop is another story.  For now, I guess the desktop stays on XP a little while longer.  :-/

Ray

---

### Post by RayJohns on 2010-04-29
After doing a little more research, I'm wondering if this is a driver/module issue with my main board.  I am running a Tyan Dual Opteron S2875 motherboard.  It has a built in SATA controller, which I have two drives on.  I also installed an IDE drive.  I've got the machine setup with drive trays, so I can turn on or off any of the drives.

I have tried to install Ubuntu 10.04 using all the drives, just the IDE drive and just one of the SATA drives.  I get the same error on all of them.  Today, I discovered this thread, which seems to relate to my issue (maybe):

[http://ubuntuforums.org/showthread.php?t=38167](http://ubuntuforums.org/showthread.php?t=38167)

My question is this:

If I install Ubuntu and it doesn't boot up, can I login with the CD "try it" disk and then add some lines to the /etc/modules file.  Would this help?  Given that the machine doesn't even boot up?  It just drops me down into what I think is a Grub terminal window or something.

Any suggestions would be most appreciated.

Ray

---

