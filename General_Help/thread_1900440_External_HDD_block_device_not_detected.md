---
title: "External HDD block device not detected"
date: 2011-12-26
forum: General Help
---

### Post by antoinethewiz on 2011-12-26
My parents got me a brand new [External Hard Drive]("http://www.seagate.com/ww/v/index.jsp?vgnextoid=29554ae6f33e7210VgnVCM1000001a48090aRCRD") this Christmas. Thing is, it was formatted for Mac (HFS+) and I use Linux and Windows only (primarily Linux). So I loaded up an old SliTaz CD, ophcrack actually :p, on the desktop computer. Went into terminal and ran the following (not copying from print, just writing from memory):
```

# fdisk /dev/sdc
(some info here...)

Command: d
Partition number: 1

Command: n
Command action p
Partition number: 1
First cylinder: 1
Last cylinder: (whatever the last one is for 1.8TB)

Command): t
Partition number: 1
Hex code: 83

Command: w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

# mkfs.ext3 -b 4096 -I 128 /dev/sdc
(blah blah blah, clean output info...)

Writing inode tables: done
Creating journal (lots of blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```
Alright, so I boot into Windows on the family desktop computer and the drive is working fine as expected (because I'm using the ext2IFS driver). Also works on the SliTaz live CD for the same computer. But when I go onto my laptop, enter Xubuntu (wubi-based), and plug in the drive; the block device isn't detected with "fdisk -l". So what's the deal here?

P.S. I've tried all 3 USB ports and have the HDD plugged into external power. Also, I'll be wiping Xubuntu from my laptop in favor of multi-booting other, less crustified, Linux distros. So solutions specific to the distro are moot.

---

### Post by llamabr on 2011-12-26
weird.  What does your /etc/fstab look like?  Also, boot up, then plug it in, wait 20 seconds, and give us:

```
dmesg | tail
```

---

### Post by antoinethewiz on 2011-12-26
I was about to do what you said but something unexpected happened when I plugged it in. It ACTUALLY auto-mounted this time. Should I return it for a new one since it seems to only want to auto-mount some of the time? Or is it possible there some intermittent issue? Oh, and do you still want that dmesg output (figured that's kind of moot right now)?

---

### Post by antoinethewiz on 2011-12-26
I'm just going to call this a ID107 error and move along. I probably goofed up somewhere. After all, I haven't had any sleep for a while so I probably did something that I thought I didn't do. In any case, if this goofs up: I'm returning it. *closed topic*

---

