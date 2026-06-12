---
title: "USB Flash Disk - Size/Formatting problems"
date: 2006-01-29
forum: General Help
---

### Post by Freddie.Ruddick on 2006-01-29
Hi,

I recently deleted a load of files from my 256MB "EasyDisk" Flash Drive. Since then nautilus reported it's filesystem as RAW, and Windows kept asking me "This drive is not formatted, would you like to format it?" After several days of this, I finally let windows format it, but the formatter reported it was a 123MB disk (The amount of free space before I deleted the files) Since then it has not been working, it corrupts whatever data I put on it.
Can anyone help?

---

### Post by Freddie.Ruddick on 2006-01-29
Attached: Screenshot of contents of drive after copying a few mp3s onto it.

---

### Post by cbudden on 2006-01-29
You drive looks bad, I would suggest reformatting again.

---

### Post by Freddie.Ruddick on 2006-01-29
Thanks cbudden,

I reformatted it with gParted to FAT16, and it no longer corrupts, but it's still only reporting as 123MB.

Any ideas, anyone?

Freddie

---

### Post by Greg2 on 2006-01-29
[QUOTE=Freddie.Ruddick]Windows kept asking me "This drive is not formatted, would you like to format it?" After several days of this, I finally let windows format it, but the formatter reported it was a 123MB disk [/QUOTE]
It sounds like Windows made a smaller partition? So I would suggest using fdisk with Ubuntu.

Insert the usb-drive then do something like:

sudo umount /media/usbdisk
sudo fdisk /dev/sda (it will ask for a command)
d (this will delete a partition) 
1 (this will delete partition #1) 
n (this will create a new partition) 
p (this will create it as a Primary partition) 
1 (Chooses partition 1) 
Enter (to take default start cylinder) 
Enter (to take default end cylinder) 
v (this will verify that the partition has been created) 
t (to change partition type) 
1 (to select partition 1) 
6 (to select FAT-16) 
w (this will save the table and exit the fdisk program)
sudo mkfs.msdos /dev/sda1

This ‘should’ work if it’s a partition problem?

---

### Post by Freddie.Ruddick on 2006-01-31
Thanks Greg2, it seems it wasn't a partitioning error. I now have a 512MB disgo

---

### Post by njzillest on 2006-03-02
you can try to defragment it.. 

then do a quick format on windows

---

### Post by Maverickprowls on 2007-02-12
The above guide to fdisk really helped me as I had no clue how to format my Disgo USB drive until just now.  I do have one overarching question however.

I have a standard 1GB Disgo, which come pre-installed with U3Safe, a utility which is neither use nor ornament to me in Linux.  

When I insert the drive it automounts both the USB disk *and* another imaginary drive called U3Safe which the system thinks is a CD-Recorder.  These are definitely separate devices as far as the system is concerned, as it mounts one from /dev/sda1 and the other from /dev/scd0

My question is, how can I completely format the Disgo to use its entire capacity as a Flash drive and stop this annoying second icon popping up on my desktop?  (I should also add at this point that if I don't unmount both drives before removing the stick, I get at least complaints from Ubuntu, and at worst file errors)


Many thanks in advance.

---

### Post by tesseract420 on 2007-02-16
I had the same problem. To avoid the problem occurring, don't delete files in windows, don't move files, just copy them (if you're using the USB storage device to move files from one machine to another). Only delete the files in Ubuntu after the copying operation is over.

SOLUTION:  format the device (not quick format) in Windows to be able to recover the space and use it/have it recognized in Ubuntu.

I was using the flash drive to back up my Ubuntu installation because I can't get an external USB hard drive to work:  oh, Ubuntu will read it, but there's not way to obtain write permissions, forget logging in as root, chmod; editing fstab, nothing but nothing worked.

---

### Post by yme on 2007-03-02
> **tesseract420 said:**
> I was using the flash drive to back up my Ubuntu installation because I can't get an external USB hard drive to work:  oh, Ubuntu will read it, but there's not way to obtain write permissions, forget logging in as root, chmod; editing fstab, nothing but nothing worked.

Big problem in Ubuntu, one of the few really annoying things about it:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=NFTS+external](http://ubuntuforums.org/showthread.php?t=217009&highlight=NFTS+external)

---

