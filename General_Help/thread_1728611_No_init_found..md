---
title: "No init found."
date: 2011-04-13
forum: General Help
---

### Post by caydence on 2011-04-13
I've installed Ubuntu 10.10 Netbook remix on my daughters EeePC 1005HAB netbook, and it was running fine until tonight.

She brought it to me, and on boot, it comes up with the GNU GRUB screen to select a boot type.  I choose Ubuntu, with Linux 2.6.35-28-generic.

It then comes up with the following:

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg
```

I did a search and found the following link:
[http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html)

When I try this in the terminal after booting from the Ubuntu Live CD, I get the following:

**sudo fdisk -l**
```

/dev/sda1 *     1  19076  153219072  83  Linux
/dev/sda2   19076  19458    3068929   5  Extended
/dev/sda5   19076  19458    3068928  82  Linux swap / Solaris

/dev/sdb1       1   3832    1006576   c  W95 FAT32 (LBA)

```
[B]
sudo fsck /dev/sda1[/B]
```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

I have no clue what I'm doing in Ubuntu and would appreciate any help I could get to get this thing running again without having to reinstall Ubuntu.

Thanks!

---

### Post by tommcd on 2011-04-14
When booting from the live CD, make sure that */dev/sda1* is *unmounted*. First run: ```
sudo umount /dev/sda1
```
Then run the *fsck* command and see if that works.

---

### Post by grvsaxena419 on 2011-04-14
> **caydence said:**
> 
[B]
sudo fsck /dev/sda1[/B]
```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

I have no clue what I'm doing in Ubuntu and would appreciate any help I could get to get this thing running again without having to reinstall Ubuntu.

Thanks!
DO NOT TRY to run fsck on a partition that is currently mounted it will lead to loss of data . Unmount the partition and then try fsck on that partition it will fix this error if you had a crash.
Try doing that and reply.

> fsck
is a tool for fixing file system errors when you do not do a proper shutdown of your system buffers may not written to the disk so it leads to an inconsistent state that prevents your system from doing a proper mount of the partition which leads to this error fixing the filesystem errors may let it overcome this problem .

---

### Post by caydence on 2011-04-14
I did the following:

```
sudo umount /dev/sda1

umount: /dev/sda1: not mounted

sudo fsck /dev/sda1

fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

Thank you for helping me out guys.  Am I correct in surmising that I just need to reinstall Ubuntu?  I did find out what she did, and that was to just let the battery die while she was using it, so it didn't successfully shut down nicely or anything.  :(

Tim

---

### Post by grvsaxena419 on 2011-04-14
> **caydence said:**
> I did the following:

```
sudo umount /dev/sda1

umount: /dev/sda1: not mounted

sudo fsck /dev/sda1

fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

Ok.
It seems that you may have mounted that partition after booting into live cd.
Try using a live cd and backup your data if data is in that partition and if there is no data just after booting into the system using live cd run 
```
sudo fsck -fy /dev/sda1 
```
after making sure the partition is not mounted. 

> 

Thank you for helping me out guys.  Am I correct in surmising that I just need to reinstall Ubuntu?  I did find out what she did, and that was to just let the battery die while she was using it, so it didn't successfully shut down nicely or anything.  :(

Tim

No you won't be needing a reinstall only a few things need to be fixed and it will work . :) One of my friend had the same problem and it got fixed easily. 
Try the above and reply .

---

### Post by caydence on 2011-04-14
Ok, booted fresh from the live cd, and ran the following:

```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted

ubuntu@ubuntu:~$ sudo fsck -fy /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

---

### Post by tommcd on 2011-04-15
What is the output of the *mount* command immediately after booting the live CD?
Something must be accessing /dev/sda1 somewhere. Do not open a web browser or any programs other than the terminal after booting from the live CD.

---

### Post by caydence on 2011-04-15
When I try this:

```
sudo mount /dev/sda1
```

I get this:

```
mount:  can't find /dev/sda1 in /etc/fstab or /etc/mtab
```

---

### Post by gandaran on 2011-04-15
> I've installed Ubuntu 10.10 Netbook remix on my daughters EeePC 1005HAB netbook, and it was running fine until tonight.

She brought it to me, and on boot, it comes up with the GNU GRUB screen to select a boot type. I choose Ubuntu, with Linux 2.6.35-28-generic.
does the netbook grub still have the old kernels and can you boot from one of them? if you can then reinstall the 2.6.35-28 kernel should fix the problem.

---

### Post by caydence on 2011-04-15
I'm not sure if I did it right.  At the GNU GRUB menu on bootup, I selected:

Ubuntu, with Linux 2.6.35-22-generic

It boots to a prompt that looks like this:

(initramsfs) _

How do I reinstall the kernel from here?

---

### Post by caydence on 2011-04-15
Got it fixed!  I did some more googling, and found some advice that said to use the Disk Utility from the Live CD to check it for errors.

It didn't find any, but it was able to mount the drive.  Then I shut it down, removed the Live CD and booted it like normal. 

Yay!

Thanks for all the help guys!

Tim

---

### Post by grvsaxena419 on 2011-04-16
> **caydence said:**
> Got it fixed!  I did some more googling, and found some advice that said to use the Disk Utility from the Live CD to check it for errors.

It didn't find any, but it was able to mount the drive.  Then I shut it down, removed the Live CD and booted it like normal. 

Yay!

Thanks for all the help guys!

Tim

Nice. :popcorn:

---

### Post by RottNKorpse on 2012-09-29
> **caydence said:**
> Got it fixed!  I did some more googling, and found some advice that said to use the Disk Utility from the Live CD to check it for errors.

It didn't find any, but it was able to mount the drive.  Then I shut it down, removed the Live CD and booted it like normal.

Thank you for sharing this finding! I did what you listed that you did with Disk Utility and it WORKED! (before I tried any of the terminal stuff, so even nicer..worked on first try)

I did have a slight difference in my solution though.

1. LiveCD / LiveUSB (my preference)
2. Dash -> Disk Utility
3. Mount Volume (try this first, if it mounts skip to #6 otherwise go to #4)
4*. Check FileSystem (this will run a check and repair anything it needs to)
5*. Mount Volume (second attempt, should work after Filesystem check if it didn't before)
6. Close Disk Utility & Shutdown/Restart your computer.
7. Remove the LiveCD (before shutdown) or the LiveUSB (after shutdown)
8. Restart (may or may not go to GRUB menu, if it does choose the first option).

*Note - steps 4. & 5. are only for if the first Mount Volume attempt fails.

That should do it! You should now be back into your desktop.

---

