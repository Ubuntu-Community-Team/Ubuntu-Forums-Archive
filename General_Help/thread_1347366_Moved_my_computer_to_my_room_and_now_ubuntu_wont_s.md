---
title: "Moved my computer to my room and now ubuntu wont start up."
date: 2009-12-06
forum: General Help
---

### Post by Rockanium on 2009-12-06
When i try to start up ubuntu it says

GRUB4DOS 0.4.4 2008-10-27, Memory: 638k / 1022M, CodeEnd: 0x42910
 [ Minimal BASH-like line editing is supported. For the first word, Tab lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits. ]

grub>_


I'm not sure whats going on or how to fix it?

---

### Post by Rockanium on 2009-12-06
Bump

---

### Post by tommynz1975 on 2009-12-06
typing

```
quit
```

should fix the trick, if you are found at the terminal  user@place:$  or the like

try 

```
xstart
```

or even the words   
```
sudo reboot
```

and see if  it boots upto the normal login screen again..

---

### Post by Rockanium on 2009-12-06
I tryed typing quit, but it came up with an error

```
Error 39: GRUB was not booted from DOS, or the backup copy of DOS at physical address 0x200000 is corrupt
```

any ideas?

---

### Post by lidex on 2009-12-06
Looks like a grub prompt. What operating systems are installed on this PC? Are you using Bcdedit or EasyBCD?

---

### Post by Rockanium on 2009-12-06
I have Windows XP and Linux Ubuntu 8.10 installed on my pc, and im not sure what Bcdedit and EasyBCD are. but i think im using Bcdedit because ive never seen EasyBCD before. (i google imaged them).

---

### Post by NoaHall on 2009-12-06
Make sure the hard drives are all plugged in correctly.

---

### Post by Rockanium on 2009-12-06
They are in pretty solid. i just unplugged them and pluged them back in, they are all good. Still not working though.

---

### Post by NoaHall on 2009-12-06
And this happened just after you moved it to your room? Is there nothing else which might have changed?

---

### Post by Rockanium on 2009-12-06
Nothing that i can think of.

Are you sure it's a hardware issue?

---

### Post by CrusaderAD on 2009-12-06
Are you using wubi? Basically, did u install inside of windows?

---

### Post by Rockanium on 2009-12-06
Yes, I installed Ubuntu inside windows.

---

### Post by issih on 2009-12-06
EDIT Whilst I was typing you mentioned wubi...thats why its grub4dos, ignore the below!

The fact that the prompt is for grub4dos leads me to suspect that you are booting from a floppy a usb key or a cd drive.

I did wonder if you had an old floppy sitting in the drive and the jolt has made it drop in to place?

Anyway check that there is no rogue media present or that the hard drive is the first boot device..

N.B. I'm probably wrong here and for some reason your setup uses grub4dos rather than normal grub, but it was just a thought :)

---

### Post by CrusaderAD on 2009-12-06
Check this out:

[http://ubuntuforums.org/showthread.php?t=1314064]("http://ubuntuforums.org/showthread.php?t=1314064")

---

### Post by Rockanium on 2009-12-06
My computer does not have a Floppy drive, and does not have any disks in the disk drive.

> Check this out:

[http://ubuntuforums.org/showthread.php?t=1314064](http://ubuntuforums.org/showthread.php?t=1314064)

i'll try those tomorow, i need to sleep for now. thanks though, i'm sure it will help if not i can download 9.10 and install that.

---

### Post by lidex on 2009-12-06
Try booting with your windows disk and use the repair function so you can at least boot into windows.

---

### Post by Rockanium on 2009-12-06
I can boot into windows, just not Ubuntu.

---

### Post by amturnip on 2009-12-06
> **Rockanium said:**
> They are in pretty solid. i just unplugged them and pluged them back in, they are all good. Still not working though.

Are you sure that each drive is plugged in to the exact same spot on the motherboard as before (when the computer was working fine)?  And (if they are daisy chained IDE drives) the drives themselves are in the same order on the chain of cables as before?

---

