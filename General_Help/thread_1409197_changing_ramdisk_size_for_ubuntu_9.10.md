---
title: "changing ramdisk size for ubuntu 9.10?"
date: 2010-02-17
forum: General Help
---

### Post by billy314 on 2010-02-17
Wine is one of the coolest things I've ever seen, but unfortunately it's still not enough to suit my needs as version 1.38 can't install any of the .NET libraries.

I'm trying to boot windows 7 on virtual box, but it seems to demand quite a bit of memory.  The "recommended" amount is 512MB, and upon checking my kernel only has 488MB total ram with not much room to spare:
```
billy@billy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           488        462         25          0         53        193
-/+ buffers/cache:        216        271
Swap:         1939         17       1921

```I've tried giving the virtual machine memory sizes in the area of 192-256MB, but that's way too much and the system locks up and aborts from it.  Memory sizes in the area of 128MB is just too small and it throws an error that there just isn't enough ram to boot.  So the only thing I can do to make this work is to increase the size of the ramdisk for my host OS so I can give more to the virtual machine (not to mention things like flash animations are horribly slow and I'd like to see them get more fluid).

I see that I have 16 ramdisks available to me:
```
billy@billy-desktop:~$ ls -l /dev/ram*
brw-rw---- 1 root disk 1,  0 2010-02-17 09:54 /dev/ram0
brw-rw---- 1 root disk 1,  1 2010-02-17 09:54 /dev/ram1
brw-rw---- 1 root disk 1, 10 2010-02-17 09:54 /dev/ram10
brw-rw---- 1 root disk 1, 11 2010-02-17 09:54 /dev/ram11
brw-rw---- 1 root disk 1, 12 2010-02-17 09:54 /dev/ram12
brw-rw---- 1 root disk 1, 13 2010-02-17 09:54 /dev/ram13
brw-rw---- 1 root disk 1, 14 2010-02-17 09:54 /dev/ram14
brw-rw---- 1 root disk 1, 15 2010-02-17 09:54 /dev/ram15
brw-rw---- 1 root disk 1,  2 2010-02-17 09:54 /dev/ram2
brw-rw---- 1 root disk 1,  3 2010-02-17 09:54 /dev/ram3
brw-rw---- 1 root disk 1,  4 2010-02-17 09:54 /dev/ram4
brw-rw---- 1 root disk 1,  5 2010-02-17 09:54 /dev/ram5
brw-rw---- 1 root disk 1,  6 2010-02-17 09:54 /dev/ram6
brw-rw---- 1 root disk 1,  7 2010-02-17 09:54 /dev/ram7
brw-rw---- 1 root disk 1,  8 2010-02-17 09:54 /dev/ram8
brw-rw---- 1 root disk 1,  9 2010-02-17 09:54 /dev/ram9

```and when I try to look into it I get this cryptic message:
```
billy@billy-desktop:~$ dmesg | grep RAMDISK
[    0.000000] RAMDISK: 17167000 - 179433a7
[    0.000000]   #4 [0017167000 - 00179433a7]          RAMDISK ==> [0017167000 - 00179433a7]

```I looked at some guides [here]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html") and [there,]("http://ubuntuforums.org/showthread.php?t=182764") but apparently my setup isn't quite the same.  I don't have a menu.lst file in boot/grub, and I don't have a grub.conf file anywhere.  So I don't know what file I'm supposed to edit for this.  Does someone have any idea how to help me out here?

---

### Post by b0b138 on 2010-02-17
There is pretty much no way you can run windows 7 on that computer, virtual or native. Not with only half a gig of ram.

---

### Post by mcduck on 2010-02-17
> **billy314 said:**
> Wine is one of the coolest things I've ever seen, but unfortunately it's still not enough to suit my needs as version 1.38 can't install any of the .NET libraries.

I'm trying to boot windows 7 on virtual box, but it seems to demand quite a bit of memory.  The "recommended" amount is 512MB, and upon checking my kernel only has 488MB total ram with not much room to spare:
```
billy@billy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           488        462         25          0         53        193
-/+ buffers/cache:        216        271
Swap:         1939         17       1921

```I've tried giving the virtual machine memory sizes in the area of 192-256MB, but that's way too much and the system locks up and aborts from it.  Memory sizes in the area of 128MB is just too small and it throws an error that there just isn't enough ram to boot.  So the only thing I can do to make this work is to increase the size of the ramdisk for my host OS so I can give more to the virtual machine (not to mention things like flash animations are horribly slow and I'd like to see them get more fluid).


The amount of memory "free" gives you has nothing to do with RAM disks. It's the amount of _actual, physical RAM your computer has_. And the only way to increase it is to buy some more RAM and plug it in.

No software tweak can make more hardware magically appear in your computer. ;)

---

