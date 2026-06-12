---
title: "CD not Mounting"
date: 2009-08-01
forum: General Help
---

### Post by razorboy5 on 2009-08-01
Hi

I have a CD with windows XP on it (hopefully)
and i'm trying to run it during boot up

however it just skips it then boots my Hard drive

then i logged onto my ubuntu and tried to see what's wrong
tried to open my CD-RW/DVD+-RW Drive however it reads

Unable to Mount Location
Can't Mount File

any help appretiated

thx

---

### Post by wojox on 2009-08-01
Can't you enter BIOS and change the boot sequence to boot from cd-rom first?

---

### Post by razorboy5 on 2009-08-01
yes in bios my USB boots first then my CD

HD is supposed to come rite after however it skips CD and goes straight to HD

---

### Post by merlinus on 2009-08-01
It may well be problems with the cd.  Can you try it on another computer?

---

### Post by wojox on 2009-08-01
Open a terminal and try:

```
sudo mount -t iso9660 /dev/scd0 /media/cdrom0
```

---

### Post by razorboy5 on 2009-08-01
$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0
[sudo] password for daniel: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

what's that mean :S?

---

### Post by wojox on 2009-08-01
It means it's a Windows CD

Run:
```
dmesg | tail
```

in terminal

---

### Post by razorboy5 on 2009-08-01
$ dmesg | tail
[  409.640043] phy0: failed to restore operational channel after scan
[  479.671841] phy0: failed to restore operational channel after scan
[  549.598433] phy0: failed to restore operational channel after scan
[  608.627058] ISOFS: Unable to identify CD-ROM format.
[  619.640585] phy0: failed to restore operational channel after scan
[  689.586917] phy0: failed to restore operational channel after scan
[  720.232073] ISO 9660 Extensions: Microsoft Joliet Level 3
[  720.283363] ISOFS: changing to secondary root
[  759.585411] phy0: failed to restore operational channel after scan
[  829.640558] phy0: failed to restore operational channel after scan

---

### Post by wojox on 2009-08-01
Extensions: Microsoft Joliet Level 3 - Yeah it's Microsoft. Do you have access to another computer to try it there?

---

### Post by razorboy5 on 2009-08-01
no at the moment but will have access to a Vista Laptop in a few hours
if i am able to get it onto a Vista Laptop can i fix this problem?
or should i just spend another dollar for a new CD? (my old brand that i've been using on Ubuntu)

---

### Post by razorboy5 on 2009-08-01
tried to burn it on a new CD
received the same result

plz help :S

must be a problem with ISO?

---

### Post by merlinus on 2009-08-01
A windows .iso???[]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by razorboy5 on 2009-08-01
yup a windows xp. iso

---

### Post by merlinus on 2009-08-01
Is this a legal copy, or something you downloaded?  If the latter, then this is the wrong place to ask for assistance, and it may be infested with all sorts of vermin.

---

