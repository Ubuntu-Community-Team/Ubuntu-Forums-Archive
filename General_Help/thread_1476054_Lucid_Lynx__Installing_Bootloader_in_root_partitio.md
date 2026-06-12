---
title: "Lucid Lynx : Installing Bootloader in root partition does not do the trick"
date: 2010-05-07
forum: General Help
---

### Post by venkykris on 2010-05-07
I have installed unbuntu 10.04.. since i dont want grub to boot my linux distros , i have installed the bootloader in the root partition (sda9 in my case with no separate partition for boot). Subsequent to successful ubuntu installation i booted using the live cd and extracted the boot loader using the following.

dd if=/dev/sda9 of=/ub.bin bs=512 count=1

Finally i edited the boot.ini (win xp) to show ubuntu in the menu which points to ub.bin.

But this doesnt seem to work... the same had worked with Mandriva 2010

Where did i go wrong ?

---

### Post by venkykris on 2010-05-10
It seems grub 2 does not support installing the loader in the non-mbr region of an hard drive. 
 
grub-install is not allowing me to specify sda9 i was forced to say sda.
 
i had to do this
 
grub-install --root-directory=/mnt/linuxroot  /dev/sda
 
This installed grub in the mbr, there by effectively overwriting the windows bootloader.

---

### Post by john newbuntu on 2010-05-10
> **venkykris said:**
> It seems grub 2 does not support installing the loader in the non-mbr region of an hard drive.
Are you sure this is true?  From what I know you should be able to install grub2 into a PBR and chainload to it from another bootloader.  
Here's a thread about a grub2 bug where there is a problem only if the partition that you install it into is a logical partition
[http://ubuntuforums.org/showthread.php?t=1339771&page=2](http://ubuntuforums.org/showthread.php?t=1339771&page=2)
Just curious on whether you tried installing it in a primary partition.

---

### Post by dino99 on 2010-05-10
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

follow 'grub 2 guide' below

---

### Post by sgage on 2010-05-10
I use the Windows 7 boot loader, with grub2 in the root partition of my Lucid installation.

I have discovered that the root partition with grub on it needs to be in a primary partition in order for it to work (mine is sda2). Given that caveat, it works just fine.

That said, I believe Vista/Win7 use a slightly different boot loader technology than XP.

---

### Post by venkykris on 2010-05-10
@John: Yes it is indeed a logical partition. But then i was able to do the same using grub 1.  I believe mandriva 2010.0 uses grub 1.
 
@sgage: unfortunately i use win xp boot loader.
 
With grub1 all i had to do is install the loader in root partion of the linux installation extract its boot record using "dd", and modify the boot.ini of win xp to load the extracted image. It was that simple with grub1, i tried to replicate the same procedure with grub 2 but it didnt work.

---

### Post by venkykris on 2010-05-25
Finally managed to nail it. I simply installed grub2 in the MBR and then extracted it using

dd if=/dev/sda of=/media/disk1/ub.bin bs=512 count=1

Then i booted using WINXP cd and restored the windows bootloader by typing "FIXMBR" in the recovery console. 

Edited the boot.ini file and added a new entry:
c:\ub.bin="ubuntu"

---

