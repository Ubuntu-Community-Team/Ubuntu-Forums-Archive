---
title: "My root directory is empty"
date: 2011-07-15
forum: General Help
---

### Post by Zeroth_0 on 2011-07-15
EDIT: Problem solved! I should have run fsck hours ago :P Thanks for the support, guys.
====

I wasn't doing anything special on my computer (Ubuntu 11.04) when it just turned off. When I rebooted I was presented with BusyBox. I'm still pretty new to linux, but it appears that root is totally empty. 

Am I screwed? Is there a way to view a log before the system crashed?

---

### Post by jramshu on 2011-07-15
It didn't give any errors when it dropped to busybox?

---

### Post by AlphaLexman on 2011-07-15
Which '**root**' are you talking about ??
```
ls /
```
or
```
ls /root
```
They are two different things!

---

### Post by Zeroth_0 on 2011-07-15
BusyBox just said "BusyBox v1.17.1 built-in shell (ash) (initramfs)"

And by root I mean /root

---

### Post by KeyserSoze93 on 2011-07-15
So that directory which was mounted as / is empty? OR it's not mounted?

Can you run "mount" is busybox and see whether the partition is mounted...

If the partition which was mounted as / (root) previously was actually EMPTY, as opposed to not mounted, I don't think you'd be able to boot at all.

Since, by default, GRUB lives there too - the busybox binary itself must be reading from somewhere...

---

### Post by Zeroth_0 on 2011-07-15
There are folders in /, but /root is empty.

"mount" returns:
rootfs on / type rootfs (rw)
none on /sys type sysfs....
none on /proc type proc....
none on /dev type devtmpfs...
none on /dev/pts type devpts...
fusectl on /sys/fs/fuse/connections type fusectl (rw, realtime)

Thanks for your help guys.

Edit- Also, by the way, I do get presented with the grub screen. Busybox loads when I select either Ubuntu or Ubuntu recovery.

Edit 2- When I boot in recovery mode, before BusyBox loads, I see:
Segmentation fault
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. try passing init= bootarg.

BusyBox[...]

---

### Post by AlphaLexman on 2011-07-15
'/root' is the $HOME directory for the $USER=root 

Although I am not familiar with busybox...

In theory, /root can be completely empty and your system should run just fine. However, you may have problems becoming the root user if it is empty.

---

### Post by Zeroth_0 on 2011-07-15
I guess I should mention the contents of /:
dev, conf, bin, init, sbin, sys, tmp, root, etc, scripts, lib64, lib, proc, var

Like I said Im new to linux, but shouldnt there be a home folder in there?

Also I edited my last reply with more info if anyone missed it.

---

### Post by AlphaLexman on 2011-07-15
> **Zeroth_0 said:**
> ...but shouldnt there be a home folder in there?
Yes, one would think so !! **BUT,**
> rootfs on / type rootfs (rw)Makes me think you are logging in as the root user, and I'm guessing you have not created any other users on your install.

---

### Post by OK-WTF on 2011-07-15
Chill brah, all ya stuffs still there.

You say your new, and your refering to shell as BusyBox... You've probably been first exposed to Linux from within your router or something.

Its all good, /root/ is generally empty from my experiences.. your shiz is gonna be in /home/(username).

Take care!

---

### Post by Zeroth_0 on 2011-07-15
> **AlphaLexman said:**
> Makes me think you are logging in as the root user, and I'm guessing you have not created any other users on your install.

I have 2 users, Zachary and Guest

> **OK-WTF said:**
> Chill brah, all ya stuffs still there.

You say your new, and your refering to shell as BusyBox... You've  probably been first exposed to Linux from within your router or  something.

Its all good, /root/ is generally empty from my experiences.. your shiz is gonna be in /home/(username).

Take care!

I hope something is mounted wrong then, because I don't have a home folder as it stands...

---

### Post by KeyserSoze93 on 2011-07-15
The fact that the file system type for / is "rootfs" and there is no partition id (e.g. /dev/sda1) means that what you're seeing in / is NOT your system root, but a minimal image designed for recovery booting (hence the stripped down shell.)

It should be that the GRUB entry has been corrupted, or something like that. But, the fact that you have no home directories or anything doesn't mean they're gone, since your not looking at your full Ubuntu / directory.

Try a live CD. This should give you a GUI and allow you to explore your partitions. I'm pretty sure you'll find your files there, which should give you some peace of mind.

Also, keep an eye out for any messages which come up when you boot the broken system. If you only get a graphical loading bar before you're dropped into busybox, look for instructions on getting GRUB to temporarily disable the splash screen - there is sure to be some message about why it's dropping you into what sounds like some kind of "failsafe mode".

---

### Post by Zeroth_0 on 2011-07-15
Thanks so much guys. Burning a CD right now.

---

### Post by AlphaLexman on 2011-07-15
Even though you say you are a newbie... obviously you can use the command line... so let's try some things to get some information !!

Does your prompt end with a '**$**' or a '**#**' ??
If it is a '**$**' ... what is the output of ```
pwd
```If not, did you mount '**/home**' on a different partition ??

[LIST]
[*]It's possible, I don't remember...
[*]Yes
[*]No
[/LIST]
Is it possible '**/home**' was encrypted ??

I am going to agree with OK-WTF in the idea that
> your shizis still there. :grin:

EDIT: Long post. KeyserSoze93 beat me.

---

### Post by Zeroth_0 on 2011-07-15
> **AlphaLexman said:**
> Even though you say you are a newbie... obviously you can use the command line... so let's try some things to get some information !!

Does your prompt end with a '**$**' or a '**#**' ??
If it is a '**$**' ... what is the output of ```
pwd
```If not, did you mount '**/home**' on a different partition ??

[LIST]
[*]It's possible, I don't remember...
[*]Yes
[*]No
[/LIST]
Is it possible '**/home**' was encrypted ??

I am going to agree with OK-WTF in the idea that
is still there. :grin:

EDIT: Long post. KeyserSoze93 beat me.

Prompt ends with neither of those. I have "(initramfs)".
"pwd" Returns "/"
/home is probably not encrypted
I don't know where I mounted home!

---

### Post by Zeroth_0 on 2011-07-15
So I found out some info running through a live CD but I dont know how to fix it.

In the disk utility, I found out that there is a warning on Reallocated Sector Count: Normalized- 97, worst- 97, threshold-36, value- 65 sectors

When booting earlier in recovery mode I noticed a "Segmentation fault" message. Im assuming theyre connected.

Anyone know how to fix this running either BusyBox or a live CD?

---

### Post by DawieS on 2011-07-15
While booted from the **Live CD**, open **Disk Utility** and run **Check Filesystem** on every partition on that disk. If all show clean, reboot from that disk.

---

### Post by Zeroth_0 on 2011-07-15
I found out which partition is not clean (obviously the one with ubuntu). Right now i'm trying to use testdisk to repair the partition.

---

### Post by Zeroth_0 on 2011-07-15
Problem solved! I should have run fsck hours ago :P Thanks for the support, guys.

---

