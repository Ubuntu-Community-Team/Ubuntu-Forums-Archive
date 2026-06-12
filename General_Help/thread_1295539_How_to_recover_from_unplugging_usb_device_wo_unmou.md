---
title: "How to recover from unplugging usb device w/o unmounting first"
date: 2009-10-19
forum: General Help
---

### Post by blur xc on 2009-10-19
A couple of times now, I've stupidly unplugged usb devices w/o unmounting first.  I guess old habits are hard to break- seems XP handles that situation a lot better than Ubuntu.  

First thing that happens- I can't "unmount" it, after the fact.  The /mount/disk (or whatever) folder continues to exist, but I can't cd into it, and I can't rmdir it.  Trying to unmout gives some fuser (IIRC) message or was it hal?  Anyway, it's stuck.  Also, I can't mount a new usb device any longer.  I trued logging out and back in again, but upon logging out I lose the use of my usb mouse and keyboard, which makes logging back in again difficult.  My only option at that point that I can see is to do a hard reset, which I hate doing.  I haven't tried seeing if a ps/2 (I think that's what they are called, the old style keyboard plug) would still work or not.  The back of my computer case in a difficult to access location, and my only old style corded keyboard is across the house on another machine.  

So far, my only fix has been to reboot.  It's frustrating, because we have a few electronic devices that charge through the usb cable, so they are plugged in to charge, I don't even think about them being mounted, and I just unplug it to use the device.  I need some AC to usb port plugs.

Also, I was wondering, is there a /etc/fstab type file that Ubuntu uses to decide how and where to mount usb devices?  It seems they are auto mounted after being plugged in, and there's got to be some kind of script that tells it to make a directory to mount it, how to mount it, and the remove the directory after unmounting.

Thanks,
BM

---

### Post by kbielefe on 2009-10-19
Have you tried the -f option to umount, i.e.:
```
sudo umount -f /media/whatever
```Depending on what version of Ubuntu you're running, you should check out either the System->prefs->removable drives and media from the main menu on the top panel or edit->preferences->media tab from any nautilus window.

FYI, windows needs you to "unmount" too, with the little "safely remove" thing in the bottom right.  Otherwise, you're eventually going to get a corrupted filesystem.

---

### Post by blur xc on 2009-10-20
> **kbielefe said:**
> Have you tried the -f option to umount, i.e.:
```
sudo umount -f /media/whatever
```Depending on what version of Ubuntu you're running, you should check out either the System->prefs->removable drives and media from the main menu on the top panel or edit->preferences->media tab from any nautilus window.

FYI, windows needs you to "unmount" too, with the little "safely remove" thing in the bottom right.  Otherwise, you're eventually going to get a corrupted filesystem.

Making me work my memory-  I think I've tried the -f option.  IIRC, it removed the mount point and it no longer shows up when running the mount command, but the usb ports stay dead, and won't mount any new usb devices until I reboot.

Windows, btw, I found out has an option to allow removal of devices w/ safely removing them first.  I noticed this on my micro sd card in xp.

BM

---

