---
title: "Can not mount internal hard drive when running from USB"
date: 2012-08-20
forum: General Help
---

### Post by tavandiver on 2012-08-20
Hello all,

I am running ubuntu from a USB drive on my computer it normally boots into XP and the XP is working fine.  I have a company computer and do not like to do my personal buisness in XP due to company policies about data monitoring.  I boot ubuntu from a USB drive my issue is that I cannot mount the internal NTFS partition on my laptop when I am running from my USB.  I have used the command 

sudo mount -t ntfs /dev/sda1 /mnt -o force

it  gives me the error invalid argument any help would be greatly appriciated I would just like to be able to access files from the my documents folder from ubuntu.

the drive shows when I do fdisk -l but does not when I do df -T

I am not completely new to linux but am new to the Forums here.

---

### Post by mikechant on 2012-08-22
Have you tried without the '-o force'?

Also, you shouldn't really mount to /mnt, you should create a subdirectory e.g.
```
sudo mkdir /mnt/ntfsdrive
```
and mount to that instead of /mnt

---

### Post by Random20210831 on 2012-08-22
I had a similar problem that I solved with the command [FONT="Courier New"]sudo mount-t ntfs / dev/sda1 / mnt[/FONT]. If that does not work try this (not the same as yours): [FONT="Courier New"]sudo mount-t ntfs/dev/sda1/mnt[/FONT] ; or this: [FONT="Courier New"]sudo mount-t ntfs /dev /sda1 /mnt[/FONT].

---

### Post by irv on 2012-08-22
What version of Ubuntu are you booting from the USB? If it is 12.04 it should just see the NTFS drive in Nautilus and you should be able to open it. It will show up as what every size it is.
Is your company running from a Network or is this a NTFS partition on the on Hard drive?

---

