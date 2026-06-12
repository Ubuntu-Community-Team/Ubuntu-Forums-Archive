---
title: "Couldn't find valid filesystem superblock"
date: 2009-07-07
forum: General Help
---

### Post by snakeman21 on 2009-07-07
My wife has a Gateway Tablet PC with Ubuntu 9.04 (after she FINALLY admitted that windows had too many problems) and she recently complained that ubuntu performs a routine check of drives too often.  I don't have this problem because I restart my computer much less frequently than her.  But she has a dual boot, and uses Windows for only her games, and ubuntu for everything else, so she reboots a lot.  So I told her I would set it so that it would only perform a routine drive check every 150 boots, or every 6 weeks, whichever came first.  I opened a terminal and typed:

```
sudo tune2fs -c 150 -i 6w /dev/sda
```

And I got this error:

```
shaina@Jaunty:~$ sudo tune2fs -c 0 -i 1m /dev/sda
tune2fs 1.41.4 (27-Jan-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.

```

So I checked gparted to ensure that her HD was indeed /dev/sda, and it was.  I restarted and logged in as root from the shell and tried again, with the same result.  Then I tried it on my computer, and got the same error!  What's going on?

---

### Post by jbrown96 on 2009-07-07
you need to specify the partition not just the decive: /dev/sda1 or whichever partition it is.

---

### Post by snakeman21 on 2009-07-07
Nope, I got the same error

---

### Post by jbrown96 on 2009-07-07
Try running fsck on the partition. You should not do this while the system is running. Do it from a LiveCd. Check out the manpage for fsck.ext4 ```
man fsck.ext4
``` It's the same program even if you used ext3 or ext2. Your command should look something like ```
sudo fsck.ext4 /dev/sda1
``` If you get an error about a bad superblock, then check the manpage for the -b option. you can then use mke2fs to find a backup superblock and update the main one, then you shouldn't have any problems running your tune2fs command.

---

### Post by snakeman21 on 2009-07-07
Well, it did a drive check earlier today, and found no errors... But I do have a live Jaunty usb on my keys... I'll do it again and let you know.

---

### Post by snakeman21 on 2009-07-07
HAHA wow, I feel stupid.  I'm experienced enough that I should have seen this.  I'm looking at her computer, running Xubuntu 9.04 from a usb stick, and realized that when I used gparted before, I didn't pay attention to the partition numbers.  I couldn've SWORN that her ubuntu partition was /dev/sda2.  Turns out that /dev/sda2 is just an extended filesystem.  Her ubuntu is on dev/sda5.  Sorry to be a bother, I can't believe I didn't notice that!


Edit:  There we go, that did it.  It helps if I open my eyes and pay attention to the details, huh?

---

