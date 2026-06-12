---
title: "GRUB Device Error after Ubuntu Installation on USB Flash Drive"
date: 2010-10-31
forum: General Help
---

### Post by robofreak on 2010-10-31
Hello all,

I've recently installed Ubuntu 10.10 on my flash drive, and now I'm having problems with GRUB.  I installed the OS through the live CD and told it to install on the flash drive.  The computer that I was using to run the CD has a hard drive with the Linux Mint OS on it, but Mint wasn't running at the time because, like I said, I was running Ubuntu 10.10 from a live CD.

After the installation was complete from the CD to the flash drive, everything seemed to work fine.  Ubuntu ran from the flash drive without a hitch.  However, when I shut down the computer, removed the flash drive, and tried to boot back into Mint, GRUB came up (which never seemed to come up during start up before, btw), and said "Error: Device not found: <a long number>", or something like that anyway, and then gave me a "grub rescue> " prompt.

I discovered that if I plug the flash drive into the computer and then start it up, GRUB loads with the option to boot Ubuntu, start a memory test, or boot into Mint.  Like I said, GRUB never seemed to pop up during start up before installing Ubuntu through this computer.  Anyway, I am able to boot Mint from the GRUB menu, and it works fine; but I'm not going to keep plugging my flash drive into the computer just so I can boot to Mint which is on the internal drive.

Help would be VERY much appreciated.  I've looked at a number of results from Google, but nothing quite matches my situation, and nothing I have tried has worked so far.

Thanks,
Robofreak

---

### Post by oldfred on 2010-11-01
The install usually installs grub to the MBR to whatever device is sda. If you installed to the externel you need to install grub to the external drive and set BIOS to boot the external. You need whatever you were booting from the internal reinstalled to the internal drive's MBR.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Often this will fix it:
Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by efflandt on 2010-11-01
You apparently forgot to put grub on the mbr of the usb.  I overlooked that when I was intentionally looking for it to put grub on a partition instead of the mbr.  It is at the bottom of the manual partitioning page of install.

You do not need to reinstall to fix it.  Just boot to Maverick on the usb and in a terminal do: **sudo grub-install /dev/sdb** (or sdf or whatever your usb is).

Then if you do **sudo update-grub**, see if it lists Mint on sda. If it does, boot from the usb (you might need to press a key during BIOS splash even if you put usb before hard drive in BIOS boot order).  Once booted into Mint from grub on the usb do: **sudo grub-install /dev/sda** (not sure if you need to do **sudo update-grub** after that).

---

### Post by robofreak on 2010-11-01
Thanks for the help guys.

Thanks for the links @oldfred.  I followed the instructions from the last link you sent, and everything works perfectly now.  :D

---

### Post by oldfred on 2010-11-01
Glad you got it working.

You can change to solved so others searching the forum may know a solution that works. See my signature if you need instructions on changing thread to solved.

---

