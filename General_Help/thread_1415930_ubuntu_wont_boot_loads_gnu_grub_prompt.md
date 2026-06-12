---
title: "ubuntu wont boot loads gnu grub prompt"
date: 2010-02-25
forum: General Help
---

### Post by hypertension on 2010-02-25
Hi, i've been running ubuntu 9.10 for about 6 weeks now and have had no issues. Today i had a power failure and upon booting up i have my options for win 7 or ubuntu as usual, so i choose ubuntu and it goes to a grub command line and i for the life of me can't figure out how to get ubuntu going. Any help would be greatly appreciated.

---

### Post by hypertension on 2010-02-25
i got this from another post
 
sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
 
I've gone and done that and found (hd0,1) not to be my ubuntu so i set it to (hd0,2) and that is my ubuntu but after i hit boot and it scrolls like mad it ends with..
 
ALERT! /host/ubuntu/disks/root.disk does not exist.  Dropping to a shell!!
 
and drops to a shell obviously.  In windows i can see c:\ubuntu\disks\root.disk
 
Any ideas what i've got to do to get this thing running again? thx

---

### Post by hypertension on 2010-02-25
dump, someone help pls

---

### Post by uRock on 2010-02-25
Please have patience while waiting for the right person to see your thread.

Thanks,
Ronnie

---

### Post by hypertension on 2010-02-25
ok thank you, i'll wait :)

---

### Post by oldfred on 2010-02-25
Because it was a power failure and is running on NTFS you may want to run chkdsk. This relates to wubi problems:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by DaveRowell on 2010-02-26
Bless you, oldfred!!!
Ubuntu wouldn't boot since an upgrade a few days ago the Sourgeforge WUBI fix rescued me.

---

### Post by oldfred on 2010-02-26
Glad you got it working :D, but that was all meierfra as he created the page I linked to. I do not know wubi at all.

---

### Post by Dr Droid on 2010-06-09
This problem happened to me when my laptop battery died.  I booted into windows and ran chkdsk [drive wubi is on:] /F to fix the issue. However the first time I tried to reboot it did not work. So I did it again and then instead of rebooting I made sure I shutdown completely. This next step may have been a little extreme and possibly is unnecessary, but I then unplugged the power supply, removed the battery, and flushed the power from the motherboard by pressing the power button down for 30 sec. and then pressing it 15 times...

Then I turned it on and it worked...

---

