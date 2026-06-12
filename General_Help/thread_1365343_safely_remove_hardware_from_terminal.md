---
title: "safely remove hardware from terminal?"
date: 2009-12-27
forum: General Help
---

### Post by dillandriskell on 2009-12-27
Hi, does anybody know how to safely remove hardware from a terminal?  I've got this script that backs up my stuff from my external hard drive and then shuts down the computer, but I need to safely remove it before I shut it down.

Is it by chance the same as unmount? I remember I did that in 9.04 without consequence.  If that's case it would be;

```
sudo umount <name of drive>
```correct?  Also, would I use the name I gave the drive or the name I get when I type

```
sudo fdisk -l
```?  Any help would be greatly appreciated.

---

### Post by 3rdalbum on 2009-12-27
When you shut down the computer, it always syncs and unmounts all drives; so you don't need to explicitly unmount the disk if you're going to issue the "halt" or "shutdown" commands. But generally you're correct; you can unmount a drive using that command. You actually give the mount point, not the device file name - so you'd use:

```
sudo umount /media/disk
```

NOT

```
sudo umount /dev/sdb
```

---

### Post by dillandriskell on 2009-12-27
Nevermind, Google answered my questions
:lolflag:

For those who Google this later; Unmount and Safely Remove is the same thing, you don't have to use the "fdisk" name.  Which is what the system refers to it as.  you just have to use the name of the drive you see on the desktop when it boots up.  To double check that go to /media/ and you should find it in there.  Then just open a terminal (**Applications > Accessories > Terminal**) and type;

```
sudo umount <name of drive>
```

---

### Post by dillandriskell on 2009-12-27
> **3rdalbum said:**
> When you shut down the computer, it always syncs and unmounts all drives; so you don't need to explicitly unmount the disk if you're going to issue the "halt" or "shutdown" commands. But generally you're correct; you can unmount a drive using that command. You actually give the mount point, not the device file name

Ahhh! I totally missed this when I replied.  Thank you! I had no clue it unmounts it for me x.x I've been researching this for like an hour now and it wasn't even necessary! haha. Thanks for the insight that makes things a lot easier.

---

### Post by phanie on 2011-02-04
> **dillandriskell said:**
> Nevermind, Google answered my questions
:lolflag:

For those who Google this later; Unmount and Safely Remove is the same thing, you don't have to use the "fdisk" name.  Which is what the system refers to it as.  you just have to use the name of the drive you see on the desktop when it boots up.  To double check that go to /media/ and you should find it in there.  Then just open a terminal (**Applications > Accessories > Terminal**) and type;

```
sudo umount <name of drive>
```

ahm,i dont think that that is correct. It's totally not the same thing. You can take off the LOL now because you're wrong.

---

