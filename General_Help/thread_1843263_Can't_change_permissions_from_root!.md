---
title: "Can't change permissions from root!"
date: 2011-09-13
forum: General Help
---

### Post by Bucky Ball on 2011-09-13
Hi all,

Weirdest problem and it seemed to just happen. Have done some searching but nothing seems to work.

I went to save a file into a directory on one of my partitions and wouldn't let me. Open Nautilus as root, right click partition and check permissions, the owner is 'root'. Try to change it from root to my user name and it refuses. Just goes to default 'root'. Can't change it even though I'm logged into Nautilus as root!

I can access files okay, read them, etc. This is only occurring on NTFS partitions by the looks but turns out and I have a heap (desktop box with four three drives).

Haven't changed fstab or anything else that I can remember. All help and ideas appreciated as I need to do some work on that box pronto and don't have a lot of time to fix it. Eek. 

Cheers. ;)

---

### Post by cj13579 on 2011-09-13
What have you got in your FSTAB file, can you post? 

NTFS does not support Linux permission settings so that is the reason you couldn't change it via Nautilus. The only way to do it (without rebooting box) is to un-mount and re-mount the drive with the creds that you want to use.

---

### Post by seawolf167 on 2011-09-13
Do you have the 'ro' (read-only) option set in /etc/fstab for that particular drive?

---

### Post by Bucky Ball on 2011-09-18
K. Just discovered something. This only happens when I try to download a .pdf from the internet to one of the NTFS partitions. Wasn't happening before. Just seemed to occur!

I'll have a bit more of a sniff around later.

/etc/fstab fine, no ro and hasn't changed at all from what it's been for ages (before this occurred). So, I'm thinking the issue not there, even more so now I have identified it further.

Sorry didn't get back to this post earlier. Flat out. Thanks for the responses.

---

