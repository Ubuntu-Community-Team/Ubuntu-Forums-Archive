---
title: "Mini SD card"
date: 2009-10-20
forum: General Help
---

### Post by H4F on 2009-10-20
A friend of mine accidentaly lost his password for minisd card. He have some important pics on it.

windows at least sees the card and is being able to mount it. but can't open explorer.

Ubuntu can't even mount it. 
dmesg:
 mmc0: error -110 whilst initialising SD card

I have other minisd card which are working fine.

How do I mount it ? may be format it ?

---

### Post by Giblet5 on 2009-10-20
> **H4F said:**
> A friend of mine accidentaly lost his password for minisd card. He have some important pics on it.

windows at least sees the card and is being able to mount it. but can't open explorer.

Ubuntu can't even mount it. 
dmesg:
 mmc0: error -110 whilst initialising SD card

I have other minisd card which are working fine.

How do I mount it ? may be format it ?


Do this ```
sudo fdisk -l
```

That'll list off all of the drives that linux can see.

Is the miniSD there? What drive and partition is it?

Let's assume that it's /dev/sdc1 and that it's listed as FAT32.

```
sudo mkfs.msdos /dev/sdc1
``` will format it.

Pull it out, waaaaaaait, and plug it back in. A Nautilus window should pop up.

If it's not FAT32, post the output of the fdisk command above and we can fix it up.

Retrieving the pics is unlikely at this point...

---

### Post by H4F on 2009-10-20
root@h4f:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4cb3870

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73162752    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10383       14934    36560747    7  HPFS/NTFS
/dev/sda4           14935       19457    36330997+   5  Extended
/dev/sda5           14935       14952      144553+  83  Linux
/dev/sda6           19085       19457     2996091   82  Linux swap / Solaris
/dev/sda7           14953       16197    10000431   83  Linux
/dev/sda8           16198       19084    23189796   83  Linux

Partition table entries are not in disk order

and for the other mini sd card which is workig :
root@h4f:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4cb3870

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73162752    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10383       14934    36560747    7  HPFS/NTFS
/dev/sda4           14935       19457    36330997+   5  Extended
/dev/sda5           14935       14952      144553+  83  Linux
/dev/sda6           19085       19457     2996091   82  Linux swap / Solaris
/dev/sda7           14953       16197    10000431   83  Linux
/dev/sda8           16198       19084    23189796   83  Linux

Partition table entries are not in disk order

Disk /dev/mmcblk0: 7969 MB, 7969177600 bytes
255 heads, 63 sectors/track, 968 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007b1e7

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         469     3767211    b  W95 FAT32
/dev/mmcblk0p2             470         968     4008217+   b  W95 FAT32



dmesg :
[97079.081130] mmc0: new SDHC card at address 5f8f
[97079.086599] mmcblk0: mmc0:5f8f SD08G 7.42 GiB 
[97079.086702]  mmcblk0: p1 p2

and for not working minisd card
dmesg:
mmc0: error -110 whilst initialising SD card

And don't say it's minisd card broken. cause nokia is asking for password and windos mounts it.

---

### Post by Giblet5 on 2009-10-20
There are two FAT32 partitions on there.

This will format it:

```
sudo fdisk /dev/mmcblk0 << !
d
2
d
n
p
1


t
b
w
!
```

You'll get a message telling you to reboot. That's pre-USB nonsense. Pull the miniSD out. Wait 5. Plug it back in.

```
sudo umount /dev/mmcblk0p1
sudo mkfs.msdos /dev/mmcblk0p1
```

---

### Post by H4F on 2009-10-20
you did not read my post. those 2 fat partitions are just an example from other mmc card which is working.

the fdisk -l with problematic mmc look like :
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc4cb3870

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73162752    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           10383       14934    36560747    7  HPFS/NTFS
/dev/sda4           14935       19457    36330997+   5  Extended
/dev/sda5           14935       14952      144553+  83  Linux
/dev/sda6           19085       19457     2996091   82  Linux swap / Solaris
/dev/sda7           14953       16197    10000431   83  Linux
/dev/sda8           16198       19084    23189796   83  Linux

Partition table entries are not in disk order

---

### Post by Giblet5 on 2009-10-20
> **H4F said:**
> you did not read my post.


Whoops. Well, it would have formatted that dual-partition mmc card into one big FAT32 partition...really REALLY fast. I rule! :/

The problematic miniSD is fried then. It happens. I hope it's not one of the smart ones with wirele$$...

NAND flash deteriorates with each write cycle. Odds-are, your friend didn't forget the password; the chip just died.

---

### Post by H4F on 2009-10-20
> **Giblet5 said:**
> Whoops. Well, it would have formatted that dual-partition mmc card into one big FAT32 partition...really REALLY fast. I rule! :/

The problematic miniSD is fried then. It happens. I hope it's not one of the smart ones with wirele$$...

NAND flash deteriorates with each write cycle. Odds-are, your friend didn't forget the password; the chip just died.

Hm bad news. 

How do you know it dies ? because of "mmc0: error -110" ? might it be just password protected ?

So the last think I will try to format it from windows.
And will post the results.


THANKS FOR YOUR HELP

---

### Post by Giblet5 on 2009-10-20
> **H4F said:**
> Hm bad news. 

How do you know it dies ? because of "mmc0: error -110" ? might it be just password protected ?

So the last think I will try to format it from windows.
And will post the results.


THANKS FOR YOUR HELP


Because linux, the most flexible device manager ever, cannot see a disk device when the card is plugged in.

Even if it were encrypted with Truecrypt, a disk device would still be listed. You couldn't get the data off intact, but you could still use the card.

That tells me A) the card is physically damaged eg, the little gold tabs are ripped away, B) the internal controller has failed eg, due to high static discharge, or C) the NAND flash memory has failed catastrophically.

No matter which of the three possibilities is the case here, the result is the same.


Who makes it? Some of the flash vendors have amazing warranties... Contact them and ask.

I just got an eleven-month-old SanDisk Cruzer pen drive replaced for free.

---

### Post by H4F on 2009-10-20
> **Giblet5 said:**
> 

Who makes it? Some of the flash vendors have amazing warranties... Contact them and ask.

I just got an eleven-month-old SanDisk Cruzer pen drive replaced for free.

The vendor is Transcend. but in the place I live it want be replaced ever :D
Physically the card is like new so excluding point A)

---

### Post by lavinog on 2009-10-20
see if photorec (part of the testdisk package) will read it.

---

### Post by H4F on 2009-10-20
> **lavinog said:**
> see if photorec (part of the testdisk package) will read it.

Nope neither works. there is no device in /dev/

---

### Post by H4F on 2009-10-20
Windows can't format it either . "Device not ready"
Now it clearly seems that mmc device is damaged in some way.

I am making thread solved.
Thanks to every one.

---

### Post by lavinog on 2009-10-20
The card is for a camera I assume.  Can the camera read anything from the card?

---

