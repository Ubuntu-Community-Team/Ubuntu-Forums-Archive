---
title: "WUBI Grub issue"
date: 2010-04-13
forum: General Help
---

### Post by Wtwine on 2010-04-13
HI

I have a dual boot Ubuntu 9.04/Windows Xp on my laptop, with WUBI installation.

I tried upgrading from grub-legacy to grub 2 in anticipation of upgrading to Ubuntu 10.04.
Now I can't boot into Ubuntu or Windows and grub rescue loads.

I have tried everything suggested on other threads but to no avail (_[http://ubuntuforums.org/showthread.php?t=1453237](http://ubuntuforums.org/showthread.php?t=1453237)_).  I need my laptop urgently for work, so here is my question:

If I uninstall WUBI via Ubuntu live Cd (accessing Windows partition via file system in Nautilus), will I be able to boot into Windows and reinstall WUBI, or will this grub problem bedevil me even with WUBI uninstalled?

Thanks

---

### Post by sh4d0w808 on 2010-04-13
I recommend to boot from a Windows CD, ask repair console and use fixmbr command, so U will be able to boot up windows XP. Then U can give another try... or a better option to install Ubuntu natively, not in Wubi.

---

### Post by Wtwine on 2010-04-13
Thanks.  Tried booting from Windows cd, but when select setup or repair options, I get error saying no drive disks were detected (???)

Incidentally, the only reason I did a Wubi installation is because I could not do a native install due to a bad sector on my hard drive.

---

### Post by Mark Phelps on 2010-04-13
Last time I checked, Wubi didn't use GRUB -- it used GRUB4DOS.  As far as I know, the only way you could "upgrade" to GRUB2 would have been to use LVM to "move" your Ubuntu installation into its own partition.

If you overwrote the MS Windows MBR trying to install GRUB2, that will prevent you from booting into Windows.

Ordinarily, you could repair this easily from a Windows CD, but if it can't even see your drive, are you sure that Windows is even still there?

Would open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one) to confirm that the Windows partition is still intact.

---

### Post by Wtwine on 2010-04-13
Hi Mark 

I did sudo fdisk -lu, and output is:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   183435839    91717888+   7  HPFS/NTFS
/dev/sda2       183435840   195365519     5964840    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

Not sure how to interpret this....

---

### Post by Mark Phelps on 2010-04-13
What this shows is that you have a primary MS Windows partition (NTFS) and a second possibly-Windows partition (FAT 32).  You have no Linux partitions on your drive -- so you can't use GRUB (as far as I know with Wubi).

The good news is that your MS Windows files, programs, and settings are probably all still intact.

However, if your MS Windows CD can't find your hard drive, I don't know what to tell you in terms of how to get a working system back -- as I've generally used that disk, booted into a command line, and ran fixboot and fixmbr to repair the XP boot loader.

---

### Post by Wtwine on 2010-04-13
Ok. So it sounds like uninstalling Wubi won't solve the issue of booting into Windows.
Thanks for your help.

---

### Post by Mark Phelps on 2010-04-14
The linked thread below has some suggestions, specifically, look at post #5:

[http://ubuntuforums.org/showthread.php?t=190892]("http://ubuntuforums.org/showthread.php?t=190892")

---

### Post by Wtwine on 2010-04-14
Mark, you are a star! (As is Adrain15 in the thread you linked me to).  
 
I'm not out of the woods yet, but booting from Super Grub Disk which I saved onto my USB has at least got me to a place where I can boot into Windows again.  However, I could not fixmbr as it says version of Windows XP on my machine is newer than the version on the cdrom.  When I try installing repair console from cd boot, it still can't find any drive disks.  Anyway, this is an Ubuntu forum, not Windows, so I'll find help for that elsewhere.
 
In the mean time, when I now boot, it says chain loading grub 2 and then gives a list of OS boot options.  None of the Debian/GNU/Linux ones work, but if I select Windows XP, it takes me to the dual boot option between Ubuntu and Windows.  The Windows boot works fine, but if I select Ubuntu, it gives a file error 15, and won't boot.  Is there a way I can roll back the chain load so that it defers back to Grub-legacy, if I boot from Ubuntu cd?
 
It feels like I am at least gettign somewhere!
 
Cheers

---

### Post by oldfred on 2010-04-14
From Ubuntu you can install a basic boot loader.

Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

This maybe what supergrub has done.

---

### Post by Mark Phelps on 2010-04-15
> **Wtwine said:**
> Mark, you are a star! 
No, I only try to help folks in trouble ...

> In the mean time, when I now boot, it says chain loading grub 2 and then gives a list of OS boot options.  None of the Debian/GNU/Linux ones work, but if I select Windows XP, it takes me to the dual boot option between Ubuntu and Windows.  The Windows boot works fine, but if I select Ubuntu, it gives a file error 15, and won't boot.  Is there a way I can roll back the chain load so that it defers back to Grub-legacy, if I boot from Ubuntu cd?
 
It feels like I am at least gettign somewhere!
 
Cheers
I'm not a Wubi expert, but last time I checked, it did not use GRUB or GRUB2, but something similar called GRUB4DOS.  I'm guessing the problem you're having in Linux is that you installed GRUB/GRUB2 -- and that is incompatible with GRUB4DOS. 

To get Ubuntu working again, you would probably have to remove the GRUB/GRUB2 stuff and replace it with GRUB4DOS -- but, I have no idea how to do that.  As I said, I'm guessing here -- and hoping someone far more expert in GRUB variants can set you straight.

---

### Post by Wtwine on 2010-04-15
Thanks.  I found various sites suggesting the fix below, but they require sh: grub>.  Unlike other folks, sh: grub doesn't automatically open when I boot.  I can type "c" which opens grub command line,  but it does not recognise below as commands.
 
How do I get into sh: grub?
 
************
[INDENT]sh:grub> linux /boot/vmlinuz-(*Your version of the kernel*) root=/dev/(*Your Windows partition*) loop=/ubuntu/disks/root.disk ro
sh:grub> initrd /boot/initrd.img-*(Your version of the kernel)*
sh:grub> boot
[/INDENT]

---

### Post by Mark Phelps on 2010-04-15
Been a while since I did this, but I believe you open an terminal and enter "sudo grub".  

From what I recall, you will then get a "GRUB>" prompt indicating that you are now in the GRUB shell.

---

### Post by Wtwine on 2010-04-18
Didn't work - grub> linux /boot/vmlinuz etc et returned an "unrecognized command" error. 

However, I had all my files backed up so Ibit the bullet and uninstalled Wubi, and then reinstalled (can't install Ubuntive natively as there is a bad sector on my hard drive).

Dual boot now works fine again, and I am happily back in Ubuntu customising it to my previous configuriation.

Won't mess with grub again until I absolutely have to!

Cheers

---

### Post by oldfred on 2010-04-18
If you have wubi with 9.10 the bug may come back:

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

