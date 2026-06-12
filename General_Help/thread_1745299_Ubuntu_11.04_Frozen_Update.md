---
title: "Ubuntu 11.04 Frozen Update"
date: 2011-04-30
forum: General Help
---

### Post by EuropaCar on 2011-04-30
Hi
I used 10.10 for a while and just tried to update to 11.04. Unfortunately, the update manager froze during the installation of packages. I gave it a long time to see if it'd recover, but it didn't. So I killed the process.
I could not then reopen update manager (nothing happened when I clicked to open it) and when I tried opening synaptic it told me another process might be using the privileges and so synaptic could not be opened.
I ran these processes in terminal and it looked like the changes that had been made to the system had prevented those programs from starting (I recall most of the errors referencing gtk, and I wonder if unity changed those references). So I could only restart the computer and of course, I can't even start ubuntu now. It is unable to mount any hard disk (in regular or safe mode).

Anyone have any idea how to solve this (short of completely reinstalling). I did back up my home folder before the upgrade but I'd rather not have to reinstall.

Thanks for any help

---

### Post by EuropaCar on 2011-05-01
any ideas?

---

### Post by NormanFLinux on 2011-05-01
You have to fix the broken errors in the terminal with configure --a as Synaptic directs.

Once the errors are fixed, run Synaptic again.

---

### Post by EuropaCar on 2011-05-01
Unfortunately, I can't even start ubuntu at this point because it is unable to mount any of the hard drives. I am in the process of reinstalling ubuntu now..

---

### Post by EuropaCar on 2011-05-03
Now, I have created a USB with ubuntu 11.04 on it, but even that won't start on this computer. I recreated the usb several times, and downloaded the file several times, so something else must be the matter. It gets up to the purple "ubuntu" loading screen and freezes (either when I try to "use ubuntu without installing" or straight up try installing).
Any ideas what could be causing this? I've never had so much trouble upgrading.

---

### Post by EuropaCar on 2011-05-04
any ideas?

---

### Post by ilantal on 2011-05-04
I also had troubles updating on both my computers. One thing good which I did do way back when was to put the "/" partition on a 12 GB partition and the "/home" on the rest of the disk (aside from a small swap partition).

That way I could format "/" without changing in any way the far more important /home. On both computers I had problems and had to reformat "/". 11.04 is really quite buggy and I hope they manage to get it under control soon. Otherwise Ubuntu will have a very bad name.

Ilan

---

### Post by EuropaCar on 2011-05-04
Thanks for the response
I might try that at some point, although my hard drive is pretty maxed out in terms of partitions. 
So I could just need a reformat, but that wouldn't explain the issue of the usb install not working

---

### Post by EuropaCar on 2011-05-05
any more ideas?
thanks in advance

---

### Post by EuropaCar on 2011-05-11
So I tried using 11.04 alternative and finally managed to get the install started (even the alternative usb stick did not boot several times). But once again, after install, 11.04 does not load even in safety mode. They both get stuck I'd say half way through the boot at a black screen. Even the alt-sysreq reisub trick doesn't snap work and I'm forced to power down manually.

Any ideas what I can do? 10.10 stick install and boot works flawlessly.

---

### Post by EuropaCar on 2011-05-11
I have just tried the 11.04 stick on my other computer (a desktop) and it works just fine. This is very frustrating, does anyone have any ideas about why it won't work on my hardware?
The stick is failing on my HP Pavilion laptop. My desktop, which the stick works on, is an ancient Dell 4600C with Nvidia graphics.

---

### Post by EuropaCar on 2011-05-12
Any ideas?
Sorry for quintuple-posting but I really have no idea where to begin with this problem (although obviously yes I have tried google first)

---

### Post by EuropaCar on 2011-05-15
Anyone?

---

### Post by ubu69 on 2011-05-20
I had the same problem.  Here is how I solved it:

Boot up with Knoppix (if you don't have this, you can find it online.  It has been a real life-saver!)

Open up a terminal.

Determine your / partition (mine is /dev/sda1).  I'll call it /dev/sdaX.

Issue these commands:

su
mount /dev/sdaX /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
cp /etc/resolv.conf /mnt/etc/resolv.conf
chroot /mnt

At this point you should be working within your actual filesystem.  Now you can get the package manager working again.  Then:

dpkg --configure -a

This will take some time and require you to answer questions occasionally.  Finally:

mount /sys
update-grub2

After this is done:

exit

This puts you back in the realm on Knoppix.  To be really thorough you should:

umount /mnt/dev
umount /mnt/proc
umount /mnt

You may get warnings saying that they are in use or some such.  Don't worry about it.

Now reboot your system.  Hope this helps!  Thanks to oldfred in [thread 1293917]("http://ubuntuforums.org/archive/index.php/t-1293917.html") for the proper commands.

---

### Post by EuropaCar on 2011-05-20
Thanks a lot for the reply!

Hmm before I actually carry out these tasks can I ask you, it looks like this is actualy solving my original problem, where 
"I could not then reopen update manager ... and when I tried opening synaptic it told me another process might be using the privileges and so synaptic could not be opened." 
Is this correct?

Because I'm not sure if this procedure would help me now, where I can't actually boot into 11.04 live usb and my current 11.04 installation (which was installed via 11.04 alternate) doesn't load

Thanks again!

---

### Post by ubu69 on 2011-05-21
I had the same original problem where the upgrade froze midway.  I had to reboot, but then I got the same messages you got where the OS could not mount the filesystem (or whatever they said).  I have had a Knoppix disk on hand for most of my Linux experience and I have bailed myself out of many sticky situations with it.

I'm not sure what exactly went wrong during the upgrade to 11.04, but the steps I followed got me into a working 11.04 shell where I was able to get everything configured and set up and then reboot successfully into 11.04.

You don't necessarily need Knoppix.  If you can make 10.10 or something boot from USB I'm sure the steps thereafter will work.

I hope to hear your success story soon!

---

### Post by EuropaCar on 2011-05-21
Thanks for your quick response!
Unfortunately, I have tried the procedure you outlined but it did not seem to change my situation.

I think your problem might be different from my current one, because I have done a fresh installation over my original one. So I no longer have issues with mounting the file system, it's just that 11.04 will not load past the purple loading screen.

But thanks for your input!

---

### Post by ubu69 on 2011-05-22
Ah...  I missed the part where you did a fresh install.  Here are a few ideas to try:

1. When you boot up, press ESC.  This will get you to the GRUB screen.  You can then try different boot options (text-only or no splash or something).  You may have to find specific ones for GRUB2.  This way you can at least see what is going on (or not) with the boot process.

-OR-

2. Try booting 10.10 from the stick and following the steps in my first post to get chrooted.  Then you can poke around the system (check logs and stuff) and make modifications.  If you figure out what you need to do, you can update-grub from there and try a restart.

As you can probably tell, I'm not a trained professional.  I spend a lot of time winging it with these things.  It certainly teaches you to think creatively.

Oh, I thought of something else.  Do you know what specific hardware is in your laptop?  If not, you could run lspci in a terminal (from 10.10 stick) and get a list of what's installed in your machine.  I bet there is one tricky little thing in there that 11.04 doesn't like.  That would at least give you something to google.

---

### Post by ubu69 on 2011-05-22
I just came across this thread:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

It explains in much detail the things I was theorizing about in my previous post.  Be patient. A solution will present itself.  Jedi wisdom for us all.

---

### Post by EuropaCar on 2011-05-27
Thanks a lot for the response!

1. I have tried several boot options (including nomodeset) but they don't seem to solve anything.
2. I'm not exactly sure what to do here, how to go about finding system logs
3. I have checked out my hardware but I am not sure where to begin figuring out what might be causing the problem. I could go through each one and search google but I dunno if it's worth it?

At one point I did manage to boot into 11.04 recovery mode. I set it to do a file system check, and when I reboot it froze at 1% (whether I boot into normal or recovery mode). 

It seems to me that it's not a graphics issue, if the computer usually locks up at the recovery menu before I can even select an option.

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

Any ideas?

---

### Post by EuropaCar on 2011-05-30
I have been searching google continuously, but I can't find anything where someone cannot even boot into recovery.

I feel like finding the solution to recovery fail would be the easiest way to diagnose, because recovery mode uses the least amount of stuff

---

### Post by pd1108 on 2011-05-30
I have had the same problem trying to upgrade 10.10 to 11.04.  on more than one occasion I've had a freezing / incomplete upgrade.  finally I did a clean install using a live CD.  then all was well.  try it thru Live CD.

---

### Post by EuropaCar on 2011-05-30
Thanks for the quick reply!

Unfortunately, even the LiveCD doesn't boot! It gets to the loading screen and freezes. This happens with 11.04 LiveCD, usb stick, and the actual 11.04 installation.
10.10 stick/cd works fine.

---

### Post by EuropaCar on 2011-06-03
Hmm any ideas?
This is so frustrating I might just give up and go back to 10.10

---

### Post by EuropaCar on 2011-06-06
So I managed to boot into the live USB ONCE. I added acpi_osi= to the menu entry and it booted fine and worked fine. However, since then, the USB will not boot, and it freezes at the loading screen as it used to. I tried adding acpi_osi= to the menu entry for the installed 11.04, but I receive the error:

booting a command list
alloc magic is broken at...

This error occurs when i choose to edit the menu entry (pressing 'e') regardless of whether or not I actually make changes to the entry...

Does anyone know why this is happening?

---

### Post by EuropaCar on 2011-06-06
I tried to load 11.04 recovery mode and received this error:

```

Stopping GNOME display manager
[   24.520437] b43-phys0 ERROR: firmware file "b43/ucode15.fw not found"
[   24.520498] b43-phys0 ERROR: firmware file "b43-open/ucode15.fw not found"
[   24.520548] b43-phys0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version.

```

I guess I'll keep looking, but it looks like most solutions to this problem require access to the desktop, which I don't have..

---

### Post by EuropaCar on 2011-06-06
So I've followed the instructions given in that error message, but it doesn't seem to have fixed the problem. The recovery mode freezes once the recovery menu pops up.

It may be helpful to know that I can access older ubuntu versions and they load and everything just fine. They do not seem to have the required drivers though, as I can't use mouse or internet..

---

### Post by EuropaCar on 2011-06-08
any ideas?

---

### Post by EuropaCar on 2011-06-08
update:

I removed the splash screen from the current 11.04 installation but for some reason it didn't even let me see the messages that normally come up (the terminal-style screen)

I removed the splash screen from the live USB and it allowed me to see the messages.
It seems it hangs on "mounting root file system..."

when I add acpi_osi= to the entry for the live USB, it gets past that step but says that the root file system needs recovery.

Which file system is it mounting? The one on the USB or the one on my hard drive? Because the 10.10 usb works just fine

---

### Post by EuropaCar on 2011-06-08
ok here is the message I get:

Begin: Mounting root file system ... [7.016800] EXT3-fs (sda5): recovery required on read-only file system
[7.016889] EXT3-fs (sda5): write access will be enabled during recovery
..etc..
stdin: error 0
..etc..

I copied the portions I thought were important

Any ideas??

---

### Post by EuropaCar on 2011-06-08
ok I am close to giving up.

I did a clean install of 10.10 from the liveusb and tried upgrading to 11.04
The installation went fine, but when I try to boot into 11.04, whether recovery mode or regular, it freezes. This time the splash screen doesn't even show up for some reason.
However, if I choose 'other ubuntu installations' (or whatever it's called) and choose the 10.10 installation, it works fine and has unity
I am actually writing this response from the installed 2.6.35-22 kernel

---

### Post by linuxinstalledfromhdd on 2011-06-08
Switch back to 10.10, and here is nice guide to get everything perfect again:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Other than that, I have no real solution to this issue you are experiencing. Sorry. :) 

I'm in the same boat as you at the moment. 11.04 was a no-good for my printer drivers, and
other important features I needed as well.  That's the way it goes, until development can hopefully
resolve those issues in the future.  They always do eventually.

---

### Post by EuropaCar on 2011-10-17
Hi guys,
bringing up an old thread. But to recap, I tried updating to 11.04 and it froze mid-update. I could not fix it and the updated ubuntu would not boot. I tried installing a fresh 11.04 and I could not even get the startup disk to boot past the purple screen. I was able to get the 11.04-alternate version to load on USB, installed it, but could not boot into the new install. Finally I gave up and switched back to 10.10. 

I've been hoping that 11.10 would somehow solve my problems, so I eagerly awaited the new release. I just created the startup disk, but lo and behold, this startup disk will not load past the purple screen, just as with the 11.04 disk!!

Does anyone have any insight into this problem? 10.10 (both the desktop and the startup disk) works perfectly. Also, the 11.10 startup disk works perfectly on another computer (an older model desktop). I am currently using an HP Pavilion dv6000 laptop.

..Any ideas???

---

### Post by EuropaCar on 2011-10-18
any ideas?

---

