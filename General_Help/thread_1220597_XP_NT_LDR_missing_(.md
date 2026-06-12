---
title: "XP NT LDR missing :("
date: 2009-07-23
forum: General Help
---

### Post by scrambledarthur on 2009-07-23
I am new to Ubuntu and I really like it.

The thing is during installation I didn't know how to work the partition slider thing so I tried to partition some files "advanced" style. I don't really know what I did when I did the advanced/manual/non-linux-guru option and I'm hoping that the files are still there.  Well, Ubuntu got installed but whenever I go to GRUB and try to boot windows XP, it sayd "NT LDR missing". 

I really don't need XP anymore, it's just that I stupidly didn't get a back up of the files because I though I'd be able to go back to windows before I made the final plunge.

I threw away the recovery disk some time ago, so what I need right now is a downloadable version of the recovery disk or some way to access the XP section of my hard drive to get the files I need.

Thanks for any help!

---

### Post by philcamlin on 2009-07-23
this can help 

[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

or you could mount the broken drive if its visible and backup from there :popcorn:

---

### Post by scrambledarthur on 2009-07-23
How would I mount the drive?

This may seem horrifically n00b, but I've heard the term being tossed around like a tennis ball. What's it mean to "mount" something?

And I was reading the link...looks like I need the CD for that. Is there anyway to restore the NT LDR without the recovery disk?

---

### Post by jocko on 2009-07-23
To mount a file system simply means that you make it accessible (so instead of seeing the hard drive as just a piece of hardware, you will see the files and folders that are stored in a file system).
Let's first see if you still have the windows partition. Open up a terminal and paste this command into it:
```
sudo fdisk -l
```Post the output from that command in this thread.

---

### Post by scrambledarthur on 2009-07-23
It asked for my password. I typed it, hit enter and this came out.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc20e3b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6297448+  12  Compaq diagnostics
/dev/sda2             785        6231    43753027+  82  Linux swap / Solaris
/dev/sda3            6232       12161    47632725    5  Extended
/dev/sda5            6232       11913    45640633+  83  Linux
/dev/sda6           11914       12161     1992028+  82  Linux swap / Solaris

---

### Post by jocko on 2009-07-23
> **scrambledarthur said:**
> It asked for my password. I typed it, hit enter and this came out.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc20e3b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6297448+  12  Compaq diagnostics
/dev/sda2             785        6231    43753027+  82  Linux swap / Solaris
/dev/sda3            6232       12161    47632725    5  Extended
/dev/sda5            6232       11913    45640633+  83  Linux
/dev/sda6           11914       12161     1992028+  82  Linux swap / Solaris
Sorry, it looks like you have overwritten your windows partition. That means all data you had on your windows partition is lost.
There may be some advanced file recovery tools that may be able to recover some of the files, but as you have installed ubuntu on top of the space where the windows partition was, it's very likely that you have overwritten many of the files so that it will be almost impossible to recover...

---

### Post by scrambledarthur on 2009-07-23
O no!

Well, thanks for everything. 

I was trying to find a script, but I figure during re-writes the material usually gets better anyways.

Well, since I botched the partition and since XP is functionally useless, is there any way to give the entire drive to ubuntu?

---

### Post by jocko on 2009-07-23
> **scrambledarthur said:**
> O no!

Well, thanks for everything. 

I was trying to find a script, but I figure during re-writes the material usually gets better anyways.

Well, since I botched the partition and since XP is functionally useless, is there any way to give the entire drive to ubuntu?
Well, as it is now ubuntu does take up almost all of your drive, except for the tiny compaq diagnostic partition and an extra swap partition (you only need one of those).

The easiest way to set up a better partition table is probably to reinstall ubuntu and let the installer use the entire drive, unless you have data in your current ubuntu partition that you want to keep. I have no idea if you need the compaq partition, I think there are some computer manufacturors that put the bios setup in a program on the hard drive in stead of on the mother board. If you are not sure the computer works without that partition, and that you can access the bios without it, it's probably best to leave it. It's just a few Gb anyway.

Edit: I just tried to calculate the size of your extra swap partition (/dev/sda2) and got it to almost 45 Gb??? That's certainly NOT necessary. But, if you are very lucky that swap partition have not been written to since you installed ubuntu, which means much of the data that occupied that space before you deleted the windows partition may still be there. So it could be worth a try to find out more about recovering files. There is a program named "photorec" and another named "testdisk" (both in the repos) which should be able to recover files. I don't know how to use them, but try searching for them here and on google.

---

