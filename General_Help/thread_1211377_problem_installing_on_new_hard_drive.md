---
title: "problem installing on new hard drive"
date: 2009-07-12
forum: General Help
---

### Post by thirdeye420 on 2009-07-12
hi all,

I'm trying to install a fresh copy from the Live cd onto another hard drive I had.  I switched the jumper on the hard drive to master when I installed it.  When i'm into step 4 of the install prompt, no drives show up when the partition program starts.  I don't think my drive is being detected, any idea why?

---

### Post by merlinus on 2009-07-12
Are there partitions on the new drive?  Can you mount it whilst running ubuntu from the live cd?

---

### Post by itsjareds on 2009-07-12
Can you post the output of fdisk -l? (That is a lowercase L, not a 1 or I)

---

### Post by merlinus on 2009-07-12
Needs to be:

```
sudo fdisk -l
```

---

### Post by itsjareds on 2009-07-12
My bad. fdisk -l without using root seems to list my USB device fine, though.

---

### Post by thirdeye420 on 2009-07-12
sudo fdisk -l does not return any output.


ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

---

### Post by itsjareds on 2009-07-12
That is strange, this should at least name the drive that you are currently booting off of. Are you using a LiveCD?

---

### Post by thirdeye420 on 2009-07-12
yes i am.  the drive i want to use is formatted in NTSF.   I used it for storage.  does that have to be wiped clean and reformatted first before trying to install?

---

### Post by itsjareds on 2009-07-12
This drive is your USB one? Yeah, you will have to reformat it to something like ext3. You could also just add an ext3 partition to it if you don't have too much data on it already.

---

### Post by thirdeye420 on 2009-07-12
no, it was a hard drive that i used for storage, not a usb stick.  what are the commands for formatting using the terminal?

---

### Post by itsjareds on 2009-07-12
Well to format the hard drive, you have to be able to see it first.

This is the command to format to ext3:
```
/sbin/mkfs -t ext3 /dev/sdaX
```
Where a is the drive, and X is the partition. In your case you'll want 1 for the partition unless you're creating two.

---

### Post by thirdeye420 on 2009-07-12
alright, i gotta figure out why it isnt detecting it.  this is really stumping me.  i have no idea why it isnt detecting it

---

### Post by itsjareds on 2009-07-12
Do you see it listed in your BIOS, or are you able to otherwise see it in another OS like Windows?

---

### Post by thirdeye420 on 2009-07-12
i dont have another os installed.  i will check my bios.  stay tuned.

---

### Post by itsjareds on 2009-07-12
Just curious, what is the make/model of your external hdd? Sometimes [people have trouble]("http://ubuntuforums.org/showthread.php?p=7603200") with specific models.

[This thread]("http://ubuntuforums.org/showthread.php?t=632792") sounds very similar to your issue, too bad it was never solved.

---

### Post by thirdeye420 on 2009-07-13
well, i checked the bios, and it isnt detecting the hard drive.  I have changed the jumpers on it, and even tried to different IDE cables and power cables, and it still cannot detect it.  I am lost as to what the issue is.  something obviously has crapped out.

---

### Post by az on 2009-07-13
Is the power connected?  Does it make any sound when you power up?  

Some BIOSes need you to rescan/refresh the list of attached devices whenever you make a change.  Maybe you need to do this?

---

### Post by sanemanmad on 2009-07-13
Hi, I had same exact issue... here's how i resolved it

on the installer disk, press F6 to edit the boot parameter and on the end of the line, enter ```
pci=nomsi
``` then hit enter. Now when you arrive to the partitioner you should have your HDD listed.

Have Fun.

If you need a better explanation, you will have to wait until i get home from work. around 7:30 AZT. I can provide screenshot then.

---

### Post by thirdeye420 on 2009-07-13
I tried doing what you mentioned above, but it did nothing.  my hard drive still won't show up in the partitioner.  Even in the BIOS, it says "IDE hard drive = none".  so I dunno what's going on.    Just to be clear, it is an internal hard drive disk.  I had the jumper on master, but switched it to cable select.  Either way, it didn't change anything.  could something be up with the motherboard?

---

### Post by itsjareds on 2009-07-13
I'm not sure.. Maybe a BIOS update is needed?

---

### Post by sanemanmad on 2009-07-14
Try changing your HDD settings in the BIOS to [AHCI] instead of IDE/SATA mode.

---

