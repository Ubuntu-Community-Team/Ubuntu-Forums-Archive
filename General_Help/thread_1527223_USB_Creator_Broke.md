---
title: "USB Creator Broke?"
date: 2010-07-09
forum: General Help
---

### Post by ShinHadoken on 2010-07-09
Tried to make my USB drive a live usb drive, but everything is grayed out/disabled. See the appended screenshot for a better idea. What in the world is the problem?

---

### Post by iponeverything on 2010-07-09
> What in the world is the problem? 

/dev/sr0 is not an image, it is your disk. 

USB Creator is for creating live/install USB stick from a live/install CD image. 

Grab one of the Desktop iso's and give yourself a decent amount space for persistent storage.

---

### Post by cbowman57 on 2010-07-09
You need to erase the USB drive, that feature is not grayed out.  For some reason there seems to be a bug though that prevents you from creating a persistence file if there is one ISO.  Download another Ubuntu iso or try copying the one you have.  After you erase the drive it should let you create the live USB.

---

### Post by cbowman57 on 2010-07-09
> **iponeverything said:**
> /dev/sr0 is not an image, it is your disk. 

USB Creator is for creating live/install USB stick from a live/install CD image. 

Grab one of the Desktop iso's and give yourself a decent amount space for persistent storage.

Good catch, I didn't see that.

---

### Post by iponeverything on 2010-07-09
I still slipped up on it. /dev/sr0 is the CD drive with the install disk in it. 

@ShinHadoken 

If all you have is the disk and not an image you can create an image from the disk like so:


```
dd if=/dev/sr0 of=~/Desktop/Ubuntu-10.04.iso
```

The image will then be on you desktop and then point USB Creator at that. 

Your thinking is correct though, as intuitively it seems like what you want to do "should" work..

---

### Post by ShinHadoken on 2010-07-09
Thanks a lot guys, built the image, erased the drive (which I don't know why I had to do, I had formatted it already anyway, trying with ext3, ext4, and just unused space) and now it's working!

---

