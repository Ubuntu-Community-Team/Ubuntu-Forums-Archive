---
title: "&quot;General error mounting filesystems&quot; After Crash 9.10"
date: 2009-11-25
forum: General Help
---

### Post by klausner on 2009-11-25
My Karmic Koala system crashed, and now I can't get it rebooted. I get past the Grub menu, then the system gets to showing the little cycling circle (kind of like a clock), and never gets past it.

All the other posts on this error seem to be Grub related, but I'm getting past that.

If I try one of my recovery kernels, I get to a pop-up menu, then a series of messages overwrite the panel at odd positions on the screen. The messages include:

> One or more of the mounts listed in /etc/fstab cannot yet be mounted

and

> General error mounting filesystems

I tried booting the Live CD (that's how I'm sending this), and manually running fsck on ALL my partitions. The worst error found was a bad timestamp, which I let it fix.

So I have a small question, and a big question:
[LIST=1]
[*]Where the heck are boot error messages logged? I can't find anythin,g in /var/log, and had to hand copy the errors off the screen. (Tried setting /etc/default/bootlogd BOOTLOGD_ENABLE=yes, but /var/log/boot is still empty)
[*]How the heck do I get this fixed!?
[/LIST]

---

### Post by mars~f on 2009-11-25
I'm seeing the same problem here.  Disturbing that the recovery shell itself is broken by this.

I haven't been able to isolate it yet, but it appears to be related to the latest kernel update, to 2.6.31-15-generic.  Selecting the previous kernel  (2.6.31-14-generic) in the GRUB boot menu eliminated the problem for me.

You can access the GRUB boot menu by holding the Shift key when the OS first starts to load.

Sorry, I don't have a LP bug number to refer to.

---

### Post by mars~f on 2009-11-25
Oops, spoke too soon.

I just tried to start the 2.6.31-14-generic recovery shell to repair a problem with the nvidia drivers on my system and I got the same message: "General error mounting filesystems".  It dropped me straight into the maintenance shell from the recovery menu.

The "Repair a broken system" recovery shell on the installer CD still works though.

---

### Post by klausner on 2009-11-25
> **mars~f said:**
> The "Repair a broken system" recovery shell on the installer CD still works though.

How do I get to the above from the CD?

---

### Post by mars~f on 2009-11-25
I found another workaround: passing in the a kernel boot parameter to put the system in runlevel 1 not only brings up the recovery menu, but the menu does not crash.

1. In the GRUB boot menu, select the 2.6.31-14 kernel
2. Hit 'e' to edit the boot parameters
3. Edit the line that reads "linux /vmlinuz-2.31-14-generic...".  Delete the "quiet" and "splash" parameters, and replace them with "1".
4. Press Ctrl-x to boot.

I filed this as bug #488462: "General error mounting filesystems" why trying to use the recovery menu
[https://bugs.edge.launchpad.net/ubuntu/+source/mountall/+bug/488462](https://bugs.edge.launchpad.net/ubuntu/+source/mountall/+bug/488462)

---

### Post by mars~f on 2009-11-25
> **klausner said:**
> How do I get to the above from the CD?

Just insert the CD into the drive and reboot.  It will boot and present you with a menu of options, one of which is "Recover a broken system".

---

### Post by klausner on 2009-11-25
OK. First of all, there is NO recovery console option on the install CD. Just Try, Install, Check Disk, Test Memory, and Boot from hard disk.

Second, your trick editing boot options in Grub did work. Thanks. But I used every test and repair option offered in the resulting menu, but when I try to do a normal boot, the system still hangs. Booting to recovery mode from grub with original options produces the same error messages noted in the [original message]("http://ubuntuforums.org/showthread.php?t=1336988").

I also, separately went through the [Grub recovery procedures]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") in the Ubuntu Wiki.

I've run fsck and efsck on all partitions, with no errors.

So I'm back to my original questions:
> **klausner said:**
> 
[LIST=1]
[*]Where the heck are boot error messages logged? I can't find anythin,g in /var/log, and had to hand copy the errors off the screen. (Tried setting /etc/default/bootlogd BOOTLOGD_ENABLE=yes, but /var/log/boot is still empty)
[*]**[SIZE="2"]How the heck do I get this fixed!?[/SIZE]**
[/LIST]

---

### Post by mars~f on 2009-11-26
> **klausner said:**
> OK. First of all, there is NO recovery console option on the install CD. Just Try, Install, Check Disk, Test Memory, and Boot from hard disk.

That might be because I am using the alternative installation disk instead of the regular installation disk (I use the alternative installation disk because it supports LVM partitions during the install).

I tried the 2.6.31-15 kernel again and it did boot correctly for me.  I get the random "waiting for swap" errors that have been reported by others, but the system continues to boot as normal despite them.

I can not think of a fix for this, so I can only suggest keeping an eye on the forums, and watching or subscribing to any Launchpad bugs that look relevant.

Best of luck,
Mars

---

### Post by klausner on 2009-11-26
OK, thanks.

Somebody else? Please?

---

### Post by klausner on 2009-11-27
Bump!

---

### Post by klausner on 2009-11-28
Bump. Help!

---

### Post by SuaSwe on 2009-11-28
Have you tried this:

"... edit and save the menu.list file to point to the latest kernel - 2.6.31-14 worked for [the author]. [He] replaced it in each line of the first Linux option given (and changed the version number to 9.10 for good measure). Careful with the spacing and punctuation. There was another menu.list file with a ~ next to it so [he] edited and saved that one too - just in case."

Source: [http://ubuntuforums.org/showthread.php?t=1308350](http://ubuntuforums.org/showthread.php?t=1308350)

I'm assuming you can access your files and everything from a live environment?

---

### Post by klausner on 2009-11-28
> **SuaSwe said:**
> Have you tried this:

"... edit and save the menu.list file to point to the latest kernel - 2.6.31-14 worked for [the author]. [He] replaced it in each line of the first Linux option given (and changed the version number to 9.10 for good measure). Careful with the spacing and punctuation. There was another menu.list file with a ~ next to it so [he] edited and saved that one too - just in case."

Source: [http://ubuntuforums.org/showthread.php?t=1308350](http://ubuntuforums.org/showthread.php?t=1308350)

I'm assuming you can access your files and everything from a live environment?

The default kernel is already 2.6.31-14. I've tried it and older versions, all with the same results.

---

### Post by qneill on 2009-12-14
Bump.

I'm having the same problem after a 9.4 -> 9.10 dist upgrade.

You can view the kernel startup messages from the maintenance shell with "dmesg".  What's missing is the output from the startup scripts.  Seems to me a "General error mounting filesystems" should leave an error message in /var/log/ somewhere, but I can't seem to find it.

Is there a way to view the boot messages even if splash is selected?

Is there a way to jack up the kernel verbosity once you can view these?
-- 
Quentin

---

### Post by qneill on 2009-12-14
Most likely related to: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)
-- 
Quentin

---

### Post by klausner on 2009-12-14
> **qneill said:**
> Most likely related to: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)
-- 
Quentin

This doesn't seem to be the same thing at all. After the mounting errors, there is no usable interface at all, just the garbled recovery console.

---

### Post by NuevaVictima on 2009-12-28
I had exactly the same problem various times to various different computers. It seems that is usual procedure to re-install the system after a crash. In such a case I don't understand why they produce such a complicated restoring system, that never works. It should be easier to say from the beggining, after a serious crash (means every 10 days) you should have available the install CD. I'm tired to installand reinstall that damned Karmic. The problem is that I use it as main system in 6 different computers, so you can imagine that my 9.10 CD is alredy worn out!!! To be honest with Win XP my life was not that busy!!!:(

---

### Post by tux821 on 2010-01-16
> **klausner said:**
> This doesn't seem to be the same thing at all. After the mounting errors, there is no usable interface at all, just the garbled recovery console.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)

**Sorry this link (mentioned earlier) is related and just fixed for me this terrible problem.**

Somehow things go wrong with the disk labels altough they are the same in my /etc/fstab and grub.cfg and worked before.

In /boot/grub/grub.cfg I replaced:

linux   /boot/vmlinuz-2.6.31-17-generic **root=UUID=a026ae5a-4c0b-42cd-8b46-b57bfb433ac7** ro   quiet splash

with

linux   /boot/vmlinuz-2.6.31-17-generic **root=/dev/sda1** ro quiet splash

No more problems on my brand new PC.
Note this is a real showstopper for people to install and use Ubuntu!

---

### Post by tux821 on 2010-01-16
> **NuevaVictima said:**
> I had exactly the same problem various times to various different computers. It seems that is usual procedure to re-install the system after a crash. In such a case I don't understand why they produce such a complicated restoring system, that never works. It should be easier to say from the beggining, after a serious crash (means every 10 days) you should have available the install CD. I'm tired to installand reinstall that damned Karmic. The problem is that I use it as main system in 6 different computers, so you can imagine that my 9.10 CD is alredy worn out!!! To be honest with Win XP my life was not that busy!!!:(

I use Debian / Ubuntu on all my systems (servers, netbook, desktop) for about 10 years now, the usual procedure is:
1) install Ubuntu
2) install updates and any application you like out of those enormous free library and sometimes a release upgrade

Ok sometimes i had some problems to solve because I like to be on the cutting edge of Linux and open source technology of course a few hardware replacements too.

All that time I listened to my friends using some other OS with frequent virus, performance and malware problems and .. re-installes.

If you crash that often, please check your hardware no OS survives on bad hardware. 
Linux / Ubuntu runs for years on good hardware, not 10 day's.
// please also check my previous post before this one.

---

