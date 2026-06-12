---
title: "Major HDD issue"
date: 2010-09-10
forum: General Help
---

### Post by vickertj on 2010-09-10
Hi all,

I have Ubuntu 9.10 installed on my machine. A little while back I installed a second hard drive for data and everything was working fine. Today, I was doing a big copy from my main disk to this secondary drive, and it completely stalled on me in the middle of the copy. I rebooted (this may have been a mistake -- I had to force the file manager to quit, even though my copy was done at a terminal not the file manager). Now, the drive will not mount. When I try to manually mount the drive, I get an error that says that /dev/sda1 is already mounted or /media/mymountpoint is busy. I created a new mountpoint and tried to mount it there, but got the same error. I tried running "sudo fsck /dev/sda1" but it gives this error:

>fsck.ext3: Device or resource busy while trying to open /dev/sda1
>Filesystem mounted or opened exclusively by another program?

The drive does show up in my BIOS still...It also shows up when I run "sudo lshw -C disk". 

Have I killed this HDD? Any ideas for how I might recover? 

If it matters: The drive is SATA, located at /dev/sda1...Formatted with ext3. Single partition. I'm running 64-bit variant of Ubuntu.

I appreciate any advice..
-T

---

### Post by vickertj on 2010-09-10
Uh, OK. This magically fixed itself. Here's what I did:

1.) Rebooted using Ubuntu CD.
2.) Mounted the problem drive from the uninstalled version of Ubuntu. It worked fine, so I figured there was a lock on the drive or something.
3.) Rebooted into installed Ubuntu.
4.) Magically fixed, even though I'd already rebooted 10 times before.

Anyways...

---

