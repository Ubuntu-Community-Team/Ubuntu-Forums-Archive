---
title: "Ubuntu not booting up"
date: 2011-01-26
forum: General Help
---

### Post by sbjaved on 2011-01-26
I have 10.10 installed and it was running fine until a power failure occurred. After that whenever you try to boot it up, grub displays the following error:

mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init.
No init found. try passing init= bootarg.

(initramfs) _

I don't have a 10.10 CD anymore so I'd be extra grateful if someone would tell me how to fix my grub. 

Thanks!

---

### Post by djeikyb on 2011-01-26
I googled the first fail line and the top two results were relevant threads from this forum:
[http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html)
[http://www.art.ubuntuforums.org/showthread.php?t=1437015](http://www.art.ubuntuforums.org/showthread.php?t=1437015)

Read through these first, then try what they mention. You need to boot into the livecd Ubuntu environment, whether you use a usb drive or a cd. Use fdisk to find which of your partitions is Ubuntu, try fixing grub. Failing that, try fscking your drive to see (and fix) any file system errors.

Start there, and keep us updated!

---

### Post by sbjaved on 2011-01-26
Don't have a LiveCD and its an old old pc...doesn't support usb installation :(

---

### Post by djeikyb on 2011-01-26
I know you don't have one right now, but can you make one at work? at a friend's house? at your neighbour's? your parents? etc. It's kind of crucial. How do you fix your system if you cannot boot at all? To clarify, it doesn't appear to be a problem with grub. It's more likely a problem with the file systems on your hard disk.

The one option you might have is maybe the initramfs has fstab and fsck. Try running the commands at the initramfs prompt. But you really need to get a livecd.

---

### Post by sbjaved on 2011-01-27
Ok. Got a live CD. Here's the output of fdisk:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbd98bd98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         894     7181023+   b  W95 FAT32
/dev/sda2             895        4865    31897057+   f  W95 Ext'd (LBA)
/dev/sda5             895        2884    15984643+   b  W95 FAT32
/dev/sda6            2885        4190    10490413+  83  Linux
/dev/sda7            4191        4770     4658818+  83  Linux
/dev/sda8            4771        4865      763056   82  Linux swap / Solaris

Tried to run a fsck. Made sure the partition wasn't mounted.

ubuntu@ubuntu:~$ sudo fsck -a /dev/sda6
fsck from util-linux-ng 2.17.2
fsck.ext4: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?

Here's the output of lsof /dev/sda6:

ubuntu@ubuntu:~$ sudo lsof /dev/sda6
lsof: WARNING: can't stat() tmpfs file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
      Output information may be incomplete.

Man, this is really bad. I can't even run a filesystem check? I didn't want to reinstall the OS and download 600MB worth of updates but looks like i'm running out of options. djeikyb?

---

### Post by Rubi1200 on 2011-01-27
Try downloading, burning, and using Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Unlike the Ubuntu CD, Slax does not try and auto-mount partitions.

I have seen people use this successfully to fsck their broken installs.

Give it a try and let me know what happens.

---

### Post by metalf8801 on 2011-01-27
You could try reinstalling grub but there is a good chance that it wont fix the problem, but it is still worth a shot. Here's a how to [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by djeikyb on 2011-01-27
EDIT: Ne'er mind, missed an important part of the post.

---

### Post by sbjaved on 2011-01-27
Thank you everybody for your help and suggestions. I've got exams coming up and I've got a dual boot environment so I'll be using windows when i need to get online. My windows installation of 2 years has suffered many power outs but has never *stopped* working...so i must say ubuntu has much work to do. I can't complain a lot since its a free OS but for an OS that markets stability, ubuntu did a poor job for me.

Thanks again for the support.

---

### Post by djeikyb on 2011-01-27
Eheh, I've encountered hundreds, if not thousands of situations where power failure totally borked Windows. I used to do testing and tech support at a backup software company : )

I see a few possibilities:

(1) Power failure borked file system in a fixable way.

(2) Power failure is coincidental, but your hard disk is dying anyway.

(3) Your hard disk has been dying, and power failure compounded the problem by borking the file system.

I'm inclined to cross out 1, because booting into a live environment should have allowed you to fsck the disk. It could be that Ubuntu livecd is being stupid, and booting into a more-advanced/less-user-friendly temporary linux (like slax, or damnsmalllinux) will let you fsck without all the user-friendly automount/detect garbage getting in the way.

Regarding option 2, does your hard disk support SMART? Can you run some diagnostics on the linux part of the drive? I don't have much experience with hard drive diagnostics, but it might be worth checking into.

It isn't schadenfreude, but my money is on 3. In my experience the computer gods enjoy pissing on fires.

---

### Post by sbjaved on 2011-01-27
I guess everybody has different experiences. I think it might be no. 3 too :) But thank God I have a second OS.

---

### Post by djeikyb on 2011-01-27
On my personal computer, I've had tons of power failures among several versions of Windows and flavours of Linux. Never had a problem the automated disk checker couldn't fix. Actually I've only ever had one drive fail, the 4gB ssd that came with my eeepc.

That said, I fully expect to wake up at three am tomorrow morning to a chorus of clicking from my four hard disks.

---

### Post by sbjaved on 2011-01-29
> **Rubi1200 said:**
> Try downloading, burning, and using Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Unlike the Ubuntu CD, Slax does not try and auto-mount partitions.

I have seen people use this successfully to fsck their broken installs.

Give it a try and let me know what happens.
Gave Slax a shot. Worked like a charm. One fsck later, I'm posting this from my Ubuntu installation *intact*

Thankyou Rubi1200.

P.S: If anybody new to Ubuntu stumbles onto this thread with the same problem, just boot up Slax (its a live CD), open Konsole and run "fdisk -l" (you won't need sudo because you're in the shell as root already)...the output will tell you which partition your linux installation is in...then run "fsck /dev/hda*" (where * is the number your partition). It will ask you to fix a bunch of stuff, just press y each time. Restart and Presto!

Thanks again everyone.

---

### Post by sbjaved on 2011-01-29
However...I do wonder why Ubuntu didn't let me run a filesystem check on an umounted partition. Is this a bug? What do you think, djeikyb?

---

### Post by Rubi1200 on 2011-01-29
> **sbjaved said:**
> Gave Slax a shot. Worked like a charm. One fsck later, I'm posting this from my Ubuntu installation *intact*

Thankyou Rubi1200.

P.S: If anybody new to Ubuntu stumbles onto this thread with the same problem, just boot up Slax (its a live CD), open Konsole and run "fdisk -l" (you won't need sudo because you're in the shell as root already)...the output will tell you which partition your linux installation is in...then run "fsck /dev/hda*" (where * is the number your partition). It will ask you to fix a bunch of stuff, just press y each time. Restart and Presto!

Thanks again everyone.
Excellent, I am really pleased this worked out for you :-)

---

### Post by djeikyb on 2011-01-29
Awesome! Glad you're back up and running!

I'd report it as a bug. Make sure it isn't already reported first, but yeah, go for it. I'm really not an Ubuntu expert, maybe someone else knows a great reason the fsck from Ubuntu livecd failed, but as far as I'm concerned, it's a bug until proven otherwise.

By the by, you can save time repeatedly hitting Y by running fsck with option y. See the man page.
```
fsck -y /dev/sda1
```

---

