---
title: "Accessing Flash Drives"
date: 2010-04-13
forum: General Help
---

### Post by jereece on 2010-04-13
How do I access a flash drive?  I am using Ubuntu 9.10.  I would think plugging it in would auto detect but that does not happen.  I have tried several different flash drives.  I stick them into a USB slot and nothing.  I went into Places.Computer and Places.Home Folder.  It's not showing there either.  I tried several different USB ports.  It appears Ubuntu can't detect USB flash drives.

Jim

---

### Post by SteveOll on 2010-04-13
Hi,


Is the USB Drive formatted?

Have you tried the USB with a LiveCD and used GParted to see if the drive is visible and can be formatted?

Is this a USB slot on the motherboard itself or one connected via a cable to a motherboard header socket, i.e. is the cable loose?

---

### Post by skyeric on 2010-04-13
they should appear in Places > Computer.
I had some problems with auto-detect a few days ago and my problem was down to using a USB hub and also the type of USB slot, if you have USB slots on the back of your computer and are using ones on the front or vice versa try switching around.

> **jereece said:**
> How do I access a flash drive?  I am using Ubuntu 9.10.  I would think plugging it in would auto detect but that does not happen.  I have tried several different flash drives.  I stick them into a USB slot and nothing.  I went into Places.Computer and Places.Home Folder.  It's not showing there either.  I tried several different USB ports.  It appears Ubuntu can't detect USB flash drives.

Jim
It definitely can detect them though.

---

### Post by codemaniac on 2010-04-13
it should be mounted in the /media directory..
cd /media;ls -l 

should list your pendrive..

---

### Post by muteXe on 2010-04-13
unplug it, and do:
```

sudo fdisk -l

```
in a terminal. That's a small 'L' by the way.  Copy the output somewhere.

now plug in the drive and run the same command. Copy the output. Paste both outputs here.

---

### Post by jereece on 2010-04-13
Now all of a sudden it appears to work.  This is the second thing in recent days that I could not get to work, then I post a message on this forum, take a break, come back and it works.  Are you guys reaching through the Internet and fixing my problems while I'm away?  :)

Thanks for the quick response.

Jim

---

### Post by skyeric on 2010-04-14
As long as it actually works in the end it's all good i guess, perhaps some setting that had got saved stopping it from working was removed after shutting down and restarting, oh well at least its working now.

Eric :)

---

### Post by quadproc on 2010-04-14
> **jereece said:**
> How do I access a flash drive?  I am using Ubuntu 9.10.  I would think plugging it in would auto detect but that does not happen.  I have tried several different flash drives.  I stick them into a USB slot and nothing.  I went into Places.Computer and Places.Home Folder.  It's not showing there either.  I tried several different USB ports.  It appears Ubuntu can't detect USB flash drives.

Jim
(I note that your system is now recognizing the flash drives)

There might be an issue with your BIOS and/or its setup.  Your motherboard documentation may say something useful.

I just recently spent a lot of time getting a USB flash drive to boot in this system.  It was recognized and auto mounted just fine but the BIOS would not boot from it.  Turns out that my BIOS is a bit buggy (it's in an ASUS P6T SE) and I have to use the F8 key during POST to get it to recognize the USB drive during bootup.

During my troubleshooting I learned from the Internet that there are a lot of quirky aspects to flash drives; generally, each different manufacturer's product has its own set of peculiarities.

I found that Gparted worked very well for initializing and cleaning out old junk from USB drives.

Good luck!

quadproc

---

