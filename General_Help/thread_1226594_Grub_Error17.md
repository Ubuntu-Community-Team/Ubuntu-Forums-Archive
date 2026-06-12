---
title: "Grub Error:17"
date: 2009-07-29
forum: General Help
---

### Post by DanSchnell on 2009-07-29
Technically its NeoGRUB, but that shouldn't matter.

When i try to boot Ubuntu from GRUB i get Error 17: File not found.  It says Kernel /boot/vmlinuz-2.6.28-14-generic root=UUIDf9a34018-88e1-4ddd-bc1e-24bbf280d7a6 ro quiet splash.

I loaded on the Live CD Checked the partition and /boot/vmlinuz-2.6.28-14-generic is there.  Why am i getting this error?

---

### Post by c0mput3r_n3rD on 2009-07-29
I had this error, and I remember having to reinstall as it's a major system error.  It happens computer startup and doesn't even load your Linux system correct?  If you can't get into your OS you have to reinstall.

---

### Post by merlinus on 2009-07-29
You can always reinstall, but why not try a few things first?

Post results of 

```
sudo fdisk -l
```

and indicate which partition linux is on.

---

### Post by kryptikos on 2009-07-29
Yeah, I agree...reinstalling is something you could do, but I personally don't run to that. You've just increased your work. Found this thread [http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")with an excellent write up to troubleshoot Grub 17 errors. Specifically check out mbwardle's message (post #9) he gives an excellent write up of how to troubleshoot:

> I got this error after installing the Ubuntu 7.10 release candidate.

The error usually happens because Linux and your BIOS detect your hard disks in different orders. GRUB tries to translate between the two using the device.map file in /boot/grub/device.map, which is automatically generated. Chances are, it guessed wrong.

In my case, I have three SATA hard disks.

My BIOS sees them as:
HDD1 - 80 GB - Windows
HDD2 - 80 GB - Linux
HDD3 - 250 GB - Media

Linux sees them as:
/dev/sda - 80 GB - Windows
/dev/sdb - 250 GB - Media
/dev/sdc - 80 GB - Linux

So it generated device.map assuming that order was correct, i.e.:
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/sdc

When the installer installed GRUB using that data, it tried to install the first part of GRUB on /dev/sda and told it to look for the OS on /dev/sdc. Unfortunately, this translated to "install on (hd0) then look for the OS on (hd2)", so it was looking for the OS on the wrong drive.

To fix it, you have to teach GRUB which order the BIOS uses. To do this, follow these steps:

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
Edit device.map (using vi or another text editor)

In my case, my new device.map was:
(hd0) /dev/sda
(hd1) /dev/sdc
(hd2) /dev/sdb

which told GRUB that sdc was really the second hard drive, not the third.

9) Run "grub --device.map=device.map"
10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)

You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that. This is what we want.

12) Edit menu.lst

You need to change references from (hd2,0) to (hd1,0), or whatever your Linux boot drive was autodetected as to whatever it is according to your BIOS.

If you get this step wrong, you'll see an error message something like:
Error 17: Cannot mount selected partition

meaning it's looking for a Linux file system on that partition, but it can't find one (because the drive device number is wrong in menu.lst).

13) Reboot

14) Celebrate or complain in this thread!

Hope this helps...

---

### Post by soupbone on 2009-08-02
I have two SATA drives with Windows XP installed on the first on.  I installed Ubuntu on the second drive and got an Error 17 after boot.  As it turns out, my motherboard has 5 SATA ports.  The second drive was connected to the 4th.  It seems that the bios only recognized the first 3 ports as possible boot drives so grub couldn't see /boot/grub at boot time yet all look ok when in linux.  I moved the second drive to port 2 and it boots fine now.  I have a M3N78-VM mother board.

I didn't see this posted anywhere as a solution, so I posted here to help someone in the future.

---

