---
title: "Finding filesystem type/repair broken filesystem."
date: 2010-07-09
forum: General Help
---

### Post by zzzname on 2010-07-09
I have a following problem:

Recently my drive with Ubuntu 9.4 has mysteriously stopped working, i.e. when I switch the computer on it informs me that GRUB didn't find the filesystem. Well, I suppose it happens.

First, I though it was due to the drive dying, but I popped it in an external enclosure and HDTune told me the drive was fine. 

Wanting to recover the files on the drive before reinstalling I first tried to mount it in said external enclosure under Windows (I have Win Ext2 driver installed which used to work just fine). This time, however, drive gets assigned a letter but upon opening it Windows popped up an error saying that the drive was not formatted and whether I would like to format it then. 

Unfazed by this streak of failures I tried to mount it under Linux but, alas, to no avail. I might have tried every single -t operator under mount command but it still won't budge and let me mount.

Now it seems I've run out of options. Any suggestions? I would be thankful.

---

### Post by audiomick on 2010-07-09
I would try putting the drive back in the computer it was in, then booting it from the live CD. You should be able to access the drive from there. If you can, then maybe your Grub is just messed up, not the drive. 
Also, if you run gparted from the live CD, you can see what sort of file system is on the drive. If it is an Ubuntu after 9.10, it is likely to be ext4.

---

### Post by zzzname on 2010-07-09
I was thinking I would be able to do that but the computer is an ultraportable with no CD/DVD and to make matters worse the USB ports stopped working ages ago. So a live-cd/usb option is out of the question.

I installed the system using netboot, you think it would be possible to repair it that way too?

---

### Post by QLee on 2010-07-09
[QUOTE=zzzname]...Now it seems I've run out of options. Any suggestions? I would be thankful.[/QUOTE]

While you have that live Cd that audiomick recommended in and booted up, try running an fsck on the unmounted partition where your system resides.

[Edit] Given what you wrote in the last post this isn't an option.

---

### Post by audiomick on 2010-07-09
> **zzzname said:**
> ... I tried to mount it under Linux but,...


This implies you can attach the drive to a Linux machine, even if you can't mount it from there. You could take QLee's advice, and run fsck on it from there.

There is some info on fsck here
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

and of course the man page
```
man fsck
```

---

### Post by zzzname on 2010-07-09
That's some great advice audiomick and QLee, much appreciated. Really, why didn't I think of it before? Thanks!

While the systems remains broken as it doesn't allow me to boot anymore spewing "error: invalid extent" and "failed to boot default entries" errors, at least I was able to mount it from other Linux machine.

So, all in all, happy ending. Cheers!

---

