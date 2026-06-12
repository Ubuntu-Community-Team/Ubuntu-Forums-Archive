---
title: "Which file system for Windows and Ubuntu?"
date: 2009-08-26
forum: General Help
---

### Post by aetherh4cker on 2009-08-26
I just bought a 1TB hard drive and I plan to be switching to Ubuntu soon, so I was wondering what would be the best file system to format the drive in so both Windows and Ubuntu can access and use it?

I would prefer to use ext3 or maybe even ext4 or xfs if I hear good things about them, but can Windows handle those?

I use Windows Vista Home Premium 64-bit.

---

### Post by rhythmiccycle on 2009-08-26
[SIZE="3"] I've read that, ext is not good for windows. (but i've never tested it my self)

> To format the new partition as fat32 file system (best for use under Ubuntu & Windows): 


check out this site:
[InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")[/SIZE]

---

### Post by spcwingo on 2009-08-26
I'd use NTFS.  It is the default filesystem in Windows NT based operating systems (including Vista).  Ubuntu has no problem reading/writing to it either.  All you need to do this in Ubuntu is a program called ntfs-3g which has been installed by default for quite a few releases now.

---

### Post by DeMus on 2009-08-26
> **aetherh4cker said:**
> I just bought a 1TB hard drive and I plan to be switching to Ubuntu soon, so I was wondering what would be the best file system to format the drive in so both Windows and Ubuntu can access and use it?

I would prefer to use ext3 or maybe even ext4 or xfs if I hear good things about them, but can Windows handle those?

I use Windows Vista Home Premium 64-bit.

What will you do on this disk? Install Windows now and after a while Ubuntu? Or ubuntu now also in dual boot? Or will it be a data disk?
What are your plans for it?

---

### Post by aetherh4cker on 2009-08-26
It will just be used to store media.  On it I'll keep all my music / movies / pictures / legally owned ROMs / etc.

Then I have two 500GB drives already... I was thinking of having one be a Linux drive, and the other be a Windows drive.

---

### Post by DeMus on 2009-08-26
> **aetherh4cker said:**
> It will just be used to store media.  On it I'll keep all my music / movies / pictures / legally owned ROMs / etc.

Then I have two 500GB drives already... I was thinking of having one be a Linux drive, and the other be a Windows drive.

Okay, so you will keep Windows and install Ubuntu as a second OS.
The new drive will be for storage purposes.
In that case format it as NTFS since that is readable and writable by both OS'es.
Use this to make it mount automatically in Ubuntu:

[SIZE="3"]**Auto mount Windows disks**[/SIZE]
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by TheNessus on 2009-08-26
a storage drive usually comes in NTFS by default, no?

---

### Post by P4man on 2009-08-26
> **aetherh4cker said:**
> I just bought a 1TB hard drive and I plan to be switching to Ubuntu soon, so I was wondering what would be the best file system to format the drive in so both Windows and Ubuntu can access and use it?

I would prefer to use ext3 or maybe even ext4 or xfs if I hear good things about them, but can Windows handle those?


You can use Ext2 and Ext3 on windows using this driver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

No viable Ext4 support though.

The benefits of Ext4 over Ext3 are minor to non existent, especially for a data storage partition.
I don't like handing microsoft a gun to shoot me by using their propriatery filesystem. Just see what is happening to TomTom.. sued over the use of .. FAT!

[http://arstechnica.com/microsoft/news/2009/02/microsoft-sues-tomtom-over-fat-patents-in-linux-based-device.ars](http://arstechnica.com/microsoft/news/2009/02/microsoft-sues-tomtom-over-fat-patents-in-linux-based-device.ars)

---

### Post by cascade9 on 2009-08-26
I agree with P4man

If you do use NTFS, be warned...its slower with linux than a 'real' linux file system.

---

### Post by GoldenSun on 2009-08-26
I would suggest using ext3 over ntfs.  I use my linux more than windows, so no real debate for me.  

But ext 3 is newer and faster than ntfs, and windows can read/write to it.  I would make life smoother in the linux than in windows, cause windows, everything is frustrating.

---

### Post by Revolutionary101 on 2009-08-26
I suggest using NTFS because you don't have to install any drivers to have it work on Windows or on Ubuntu. Ext3 and Ext4 have major performance advantages over NTFS but you probably wouldn't notice them on a storage only drive.

---

