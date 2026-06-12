---
title: "Mouting Vs. Ejecting?"
date: 2009-12-19
forum: General Help
---

### Post by mahela007 on 2009-12-19
What is the difference between mounting and ejecting?

---

### Post by akoskm on 2009-12-19
> **mahela007 said:**
> What is the difference between mounting and ejecting?

mount - mount a file system
eject - eject removable media

2 totally different and definite operations.

---

### Post by 3rdalbum on 2009-12-19
Ejecting is the same as unmounting - so mounting is the opposite of ejecting.

---

### Post by Grenage on 2009-12-19
When you mount something, you make it usable in the operating system.  You assign it a mount point where it can be accessed.  When you unmount something, you are simply telling the operating system that it's no longer to be used.

Eject is telling the operating system that not only is the media not to be used, but that it doesn't even exist any more.

Bottom line, in the case of USB drives:  Eject if you don't want to use it any more (you're going to take it out), unmount if you simply want to make changes to the filesystem on it, or plan to use it again before it's removed.

---

### Post by audiomick on 2009-12-19
Note: it is important with removable drives  and other memory devices to eject them when you are finished, to give the system a chance to say "I am not finished writitng yet!". Interrupting a write procedure can mess up the file system on the device.

---

### Post by mahela007 on 2009-12-19
my bad.. I should have said 'unmouting' vs. ejecting.. so basically they are the same thing?

---

### Post by mahela007 on 2009-12-19
What is the technical difference? What does linux do when I say the drive doesn't 'exist' any more?i.e I eject it?

---

### Post by Grenage on 2009-12-19
No.  If you eject a drive, you won't be able to use it again unless you physically remove it and insert it again (well, for all intents and purposes).

If you unmount a drive, you can simply mount it again (unless you've removed it).

If you are done with the disc, eject.  If you might need it again before you remove it, unmount.

> What is the technical difference? What does linux do when I say the drive doesn't 'exist' any more?i.e I eject it?

I covered this in my previous post.

---

### Post by mahela007 on 2009-12-19
well, what I meant was, what does the operating system change in order to 'tell' itself that the drive has been removed?

---

### Post by Grenage on 2009-12-19
Ah I see.  Of that I am not really sure, but I think it cuts power to the USB port when you eject a device.

---

### Post by benji72 on 2009-12-22
When you "eject" a device, power is still supplied to the device.  This allows the device to still be able to interact with the system so that the system can retrieve information and what-not from it, which I guess can somehow be useful.

---

### Post by mahela007 on 2009-12-23
Then what IS the difference between the ejecting and unmounting?

---

### Post by Grenage on 2009-12-23
> When you "eject" a device, power is still supplied to the device. This allows the device to still be able to interact with the system so that the system can retrieve information and what-not from it, which I guess can somehow be useful.

Eject kills the power to the port!

---

### Post by 3rdalbum on 2009-12-23
When you right-click on a drive's icon in Karmic, you get three options:

1. Eject
2. Unmount
3. Safely Remove.

All three of these options merely unmount the drive. I believe with optical media the "Eject" option will actually push the tray out.

On Linux, when you mount a drive the contents appears in the "mount point" - that is, a folder inside /media that appears to contain the contents of your drive. When you unmount the drive, the contents (and sometimes the mount point) will disappear too.

---

### Post by mahela007 on 2009-12-23
So why include all these 3 options?

---

### Post by redmk2 on 2009-12-23
> **mahela007 said:**
> So why include all these 3 options?
Because CD's and DVD's unmount differently from memory sticks.

CD's and DVD's need be ejected from the device and memory sticks you need to remove manually.

---

### Post by mahela007 on 2009-12-24
What do you mean CD's and DVD's unmount differently?

---

### Post by lewisforlife on 2009-12-24
There have to be a million threads on this subject already, but here goes again.

> **mahela007 said:**
> So why include all these 3 options?

I will give an example.  I have a phone that shows up as a mass storage device when plugged in, and the phone is also recharged.  Generally I want to unmount my phone when I am done using it as a device so that my it will still get power, but so my phone can access the flash memory within it, which it can't do when it is mounted.

Sometimes though, if my phone has been plugged in for 50 hours straight, and I have been using it, and the battery is hot, I may want to eject it so that the USB port does not supply any power to it.  It is all about choice, you have a choice to supply power to it, but not have a file system mounted by unmounting it, or if you do not want power supplied to your device, you can eject it, and unplug it if you like.  Also, some devices don't mount as a filesystem, for instnance, if you have an electronic device that just uses the USB port to recharge, it is not mounted, so you can't unmount it when you are done with it, you have to eject it to stop power to it.

I mount my phone when I want to access the file system.  Do you now get the difference between mounting, unmounting, and ejecting?

---

### Post by mahela007 on 2009-12-24
thanks for the explanation... but then what is 'safely remove'?... (yes.. I am a very stubborn poster ;-) )

---

### Post by redmk2 on 2009-12-24
> **mahela007 said:**
> thanks for the explanation... but then what is 'safely remove'?... (yes.. I am a very stubborn poster ;-) )

Safely remove means you have unmounted the drive and it is avaiable for removal.

If you remove a flash drive without first unmounting it, you run the chance of corrupting the data.  Open files may not be written to properly before you physically disconnect the device.

It may help to think of the needs of the media.  Optical drives (CD's and DVD's) require different means to remove the media than flash drives.  In any event you should unmount the drive safely before removing the media.

---

