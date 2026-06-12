---
title: "Getting errors when booting iso's/.img from USB? Use this method"
date: 2011-09-11
forum: General Help
---

### Post by Dlambert on 2011-09-11
If you are having difficulties burning and booting an iso or img file from a usb drive, try this method.

But first I recommend that you download your iso or img via torrent, to prevent corruption if possible.

Open a terminal and type:
```
cd /home/YOURUSERNAME/Downloads
```Replace USERNAME with your username, and Downloads with the folder in which your iso is located.

Then, with the usb drive inserted:
> sudo fdisk -lTo detirmine when your USB drive is mounted (for me it was SDB)

Then:
> sudo dd if=*NAME OF ISO* of=/dev/sd[REPLACE WITH THE RESULT OF PREVIOS STEP]DO NOT, I repeat DO NOT, enter something like sdb1. Because it will not work, you have to use the root of the drive. Which would be sdb instead. 

This guide comes straight for mips, I just thought I'd post it for everyone to see, I take no credit.

---

### Post by Dlambert on 2011-09-24
If your having problems doing this, use:

```
su
```

And enter your password to use root

---

### Post by haqking on 2011-09-24
> **Dlambert said:**
> If your having problems doing this, use:

```
su
```

And enter your password to use root

Ubuntu root is locked by default.  And it is preferrable to use sudo or gksudo for root privelege.

see [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

as for using a .iso or .img file  for USB, easier to download and use Unetbootin, it is in the repos.

---

### Post by oldfred on 2011-09-24
This works for hybrid ISOs which some other distributions already have. Note that it totally erases your flash drive.

The daily ISOs for the Ubuntu Oneiric development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs.
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)

---

### Post by Dlambert on 2011-09-28
Yes, but it also works on other Linux distributions.

---

