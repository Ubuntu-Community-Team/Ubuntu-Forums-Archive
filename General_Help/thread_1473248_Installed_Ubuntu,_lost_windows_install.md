---
title: "Installed Ubuntu, lost windows install"
date: 2010-05-05
forum: General Help
---

### Post by GrimCrimson on 2010-05-05
Tonight I decided I would install Ubuntu on my laptop, which also has windows 7 installed on it.  

I have two hard drives in the laptop, one 160GB in the "primary" bay and a 320GB in the "secondary" bay.  My partioning got a bit screwed up when in installed windows (mostly because of laziness on my part) and the Ubuntu install just made the mess even bigger.  

The way it was setup before the Ubuntu install was this:

[LIST]
[*]Windows has a 55GB partition on the 320GB drive (yeah for some reason i am booting from the secondary drive, hence the quotes).  This partition is bootable.
[*]Following the windows partition is a 255GB storage partion, NTFS
[*]There was 37GB of unused space at the beginning of the 160GB drive
[*]There is a 122GB storage partition, NTFS
[*]Both dives have a 49MB dell utility partition, FAT
[/LIST]
As you can probably tell, I really butchered the partitioning when installing windows.

I took the 37GB partition on the first disk and split it into a 33GB partition for Ubuntu and a 4ish GB partition for the swapfile.

After Ubuntu was installed it worked fine, but I cannot see the windows install in GRUB.

This brings me to my question:  How can I make GRUB see my windows install that is on a separate hard drive than the Ubuntu install?

I know I could resolve the issue by wiping everything and doing it properly, but I really dont want to have to do this if there is an easy fix that will let me boot windows again.

All of the windows files and whatnot are still there because I can see them from inside Ubuntu.

Thanks in advance and sorry if my post is a bit disorganized.

---

### Post by dino99 on 2010-05-05
look at sticky threads: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

there are tons of same problems and be already answered, search first

---

### Post by GSF1200S on 2010-05-05
> **GrimCrimson said:**
> Tonight I decided I would install Ubuntu on my laptop, which also has windows 7 installed on it.  

I have two hard drives in the laptop, one 160GB in the "primary" bay and a 320GB in the "secondary" bay.  My partioning got a bit screwed up when in installed windows (mostly because of laziness on my part) and the Ubuntu install just made the mess even bigger.  

The way it was setup before the Ubuntu install was this:

[LIST]
[*]Windows has a 55GB partition on the 320GB drive (yeah for some reason i am booting from the secondary drive, hence the quotes).  This partition is bootable.
[*]Following the windows partition is a 255GB storage partion, NTFS
[*]There was 37GB of unused space at the beginning of the 160GB drive
[*]There is a 122GB storage partition, NTFS
[*]Both dives have a 49MB dell utility partition, FAT
[/LIST]
As you can probably tell, I really butchered the partitioning when installing windows.

I took the 37GB partition on the first disk and split it into a 33GB partition for Ubuntu and a 4ish GB partition for the swapfile.

After Ubuntu was installed it worked fine, but I cannot see the windows install in GRUB.

This brings me to my question:  How can I make GRUB see my windows install that is on a separate hard drive than the Ubuntu install?

I know I could resolve the issue by wiping everything and doing it properly, but I really dont want to have to do this if there is an easy fix that will let me boot windows again.

All of the windows files and whatnot are still there because I can see them from inside Ubuntu.

Thanks in advance and sorry if my post is a bit disorganized.

What version of Ubuntu is installed (9.10, 10.04)? Give me the output of the following command run in a terminal:
```
sudo update-grub
```

Also, go to the following website and download the script to your desktop:
[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")
Then, run the script as follows:
```
sudo bash ~/Desktop/boot_info_script055.sh
```
It will create a file called RESULTS.TXT- please post the contents of that file here.

---

### Post by GrimCrimson on 2010-05-05
Sorry I forgot to mention I am running Ubuntu 10.04

Here is the output of sudo update-grub:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
“Adding Windows”
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Embedded on /dev/sda6
done

It says adding windows because I have tried to mess around with grub and add in a custom entry.  I created a file called 11_Windows in /etc/grub.d  -  here is the contents of that file:

#! /bin/sh -e
echo “Adding Windows” >&2
cat << EOF
menuentry “Windows 7” {
insmod ntfs
insmod chain
insmod drivemap
set root=(hd1,2)
drivemap -s (hd0) (hd1)
chainloader +1
}
EOF

I have attached the results of sudo bash ~/Desktop/boot_info_script055.sh

I should mention that the XP install that is listed is actually a Dell MediaDirect partition, not windows XP

Thanks a lot for helping me out.

EDIT:

It appears that I have lost my windows MBR (not sure if this matters or not)
I found this out by running the following from the grub command prompt:

```
insmod ntfs
set root=(hd1,2)
chainloader +1
boot
```

it is looking more and more like a complete reformat is my best option.

---

### Post by GrimCrimson on 2010-05-05
Disregard, got it booting to Ubuntu again.

---

### Post by oldfred on 2010-05-05
Your windows file does not look complete. it only has
/Windows/System32/winload.exe

It is missing additional files that may be in the same partition or in the windows 100mb boot partition which you do not have. Ithink these are the two files :
/bootmgr /Boot/BCD

You probalby have to run windows repairs on that install.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by GrimCrimson on 2010-05-05
Thanks for the help oldfred.

I had tried that before and it led to neither system being bootable.  GRUB didnt load, all I got was a screen that said missing operating system.  I reinstalled GRUB and got back to where I could only boot Ubuntu.

I have officially given up and think it is better to do this properly instead of mickey mousing something that works.  I am going to reformat.

Thanks for all the help guys, I will most likely be back at some point.

---

