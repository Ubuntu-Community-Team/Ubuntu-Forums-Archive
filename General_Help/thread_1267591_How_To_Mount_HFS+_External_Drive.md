---
title: "How To Mount HFS+ External Drive?"
date: 2009-09-15
forum: General Help
---

### Post by Daug on 2009-09-15
Hello--

I'm running Ubuntu Hardy on a x86 Toshiba laptop, and I'd like to mount my 500GB Western Digital "MyBook" drive, via USB.  The external drive is formatted HFS+ (journaled).  I don't need write access, just read access so that I can copy some files to the laptop.  I don't think there's an easy (GUI) way to do this; but what would the steps be through terminal to get this drive mounted on my desktop?

Thanks!

---

### Post by zvacet on 2009-09-16
You are running Hackintosh don't you?I don't believe you will get support for pirated OS.

---

### Post by Daug on 2009-09-16
No; I'm not running any pirated OS.  My 500GB external drive is formatted HFS+ because it's also mounted on a mac mini that acts as my media server.  The large external drive is storage for my media.  I would like to copy a few of the files from the external drive to my ubuntu laptop (just requires read permissions, correct?), but am having trouble finding what the exact steps are for this.  Most of my web research has yielded comments about how to get write permissions working (turn off journaling, etc.), but I haven't found the simple steps to just mount the HFS+ drive as read only, and copy some files over.  I'm hoping this isn't to difficult.. any help is greatly appreciated!

Ubuntu rocks!
-Daug

---

### Post by ChumleyEX on 2009-09-16
I found this on a google search. 

[http://ubuntuforums.org/showthread.php?t=98286](http://ubuntuforums.org/showthread.php?t=98286)

I'm suprised you can't just plug it in and go.

---

### Post by Daug on 2009-09-16
Thanks Chumley--

I guess now I'm wondering...

1) Do I need to unmount the drive from the mini (OS X) first?

2) I suppose then I would run something in Terminal like:

mount -r /dev/sdb6 /media/usbdisk -t hfsplus

However, what would I replace "sdb6", "media", "usbdisk", "-t", & "hfsplus" with, for my setup?  And do I need all of these statements? I've failed to get clarity on this after researching the [Mount Command]("http://linux.about.com/od/commands/l/blcmdl8_mount.htm"), so any help is greatly appreciated.

Thanks again

---

### Post by ChumleyEX on 2009-09-16
Unmounting is always a good idea it seems. 

try 

```
umount /dev/sdb
```

not sure if you have to do each partition or not but in ubuntu it's that simple.

---

### Post by Daug on 2009-09-16
I can unmount the volumes from the mini in OS X first, by just dragging them to the trash.

Then, maybe (hopefully) the drive will mount itself when I plug it into the ubuntu laptop.

If not, though, should I try something like:

```
mount -r /dev/sdb6 /media/usbdisk -t hfsplus
```

Also, do I need all of those arguments, and what do they refer to?

If it does mount, it should either be an icon on the desktop, or available at /etc/mnt, right?

Thanks again for your help

---

### Post by Daug on 2009-09-16
I just found a thread that I think describes exactly how to mount HFS+ in Ubuntu:

[http://ubuntuforums.org/showthread.php?p=2346494#post2346494]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494")

It has other good info too.  I will try this when I get home.

Thanks for the help so far.

---

