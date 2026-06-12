---
title: "Fix hdd that became raw"
date: 2010-03-30
forum: General Help
---

### Post by marc sauve on 2010-03-30
I recently installed Linux Mint on a friend's PC, everything fine there but, I forgot to remove my 1 TB external Harddrive. Now it is not accessible, it is now RAW it was NTFS . I used it to transfer the files that my friend wanted to keep.  I NEED HELP   over 600 movies 14000 mp3's I really don't want to lose it all!   I use Linux Mint 8, I don't understand what's wrong, so I can't fix it without some help.

---

### Post by LoneWolfJack on 2010-03-30
when you plug in the drive, does mint see it and/or display the contents?

---

### Post by marc sauve on 2010-04-01
No it shows up but, I can't access it. It says this drive needs to be formatted. I tried a recovery program but I need 700 gigs of free space that I don't have.

---

### Post by Chronon on 2010-04-01
Here are some things to try:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by john newbuntu on 2010-04-01
Did you try and mount it manually as NTFS?

mkdir /mnt/drv
mount -t ntfs /dev/hdb /mnt/drv

(presuming /dev/hdb to be your 1TB HD.)

Can you mount it back to the Mint Gloria machine and "safely unmount" the drive?

---

### Post by egalvan on 2010-04-01
> **marc sauve said:**
> No **it shows up **but, I can't access it.

It shows up? Where does It shows up?
Can't access it? How are you trying to access it?

>  It says this drive needs to be formatted.

What says that the drive needs to be formatted?

>  I tried a recovery program but I need 700 gigs of free space that I don't have.

What recovery program did you try?
What told you that you need 700GB of space?

Run gparted to see what it says about your drive.
post a screen-shot of gparted showing your "bad" drive selected.

run 
```
 fdisk -l

```
and post the results.

Thank you.

---

### Post by marc sauve on 2010-04-01
results


marc-laptop marc # mount -t ntfs /dev/sdb1 /mnt/drv
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

