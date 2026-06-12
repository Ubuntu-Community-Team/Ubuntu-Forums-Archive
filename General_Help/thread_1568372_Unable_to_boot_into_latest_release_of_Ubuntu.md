---
title: "Unable to boot into latest release of Ubuntu"
date: 2010-09-05
forum: General Help
---

### Post by virsto on 2010-09-05
I have a dual-boot system (Windows 7 and Ubuntu 10.04) both 64-bit running on an HP pavilion laptop. I installed this dual-boot system only a few months ago and have continually added some new packages and updates with very few problems. However, now something has happened that really baffles me --- An error in the bootup process that I have never seen before and one that I have been unable to solve. 

The problem --- I had been doing some programming (in Python) and after having the laptop on for several hours, I did a graceful shut down. Then, the next morning I turned on my laptop and the following is what happened:

<The following two selections are displayed>
[B]Windows
Ubuntu[/B]
********************************************************************
<A. If Ubuntu is selected then the following is displayed at the top>
[B]GNU GRUB version 1.98-1ubuntu5

Ubuntu, Linux 2.6.32-24-generic
Ubuntu, Linux 2.6.32-24-generic (recovery mode)
Ubuntu, Linux 2.6.32-23-generic
Ubuntu, Linux 2.6.32-23-generic (recovery mode)
Ubuntu, Linux 2.6.32-21-generic
Ubuntu, Linux 2.6.32-21-generic (recovery mode)[/B]
********************************************************************
<B. If the first of the six is chosen the following message is displayed>
[B]Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the 'fuser' command.
Could not mount the partition /dev/sda2. This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or exiting it. To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows. After this you should be able to reboot again and resume the installation. 
(filesystem = ntfs, error code = 16)

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _[/B]
********************************************************************
<C. If the second of the six is chosen the following is displayed>
...
...
...
[  [B]17.065881 CE: hpet increasing min_delta_ns to 15000 nsec
[/B]
<where ... represents system generated messages, and then the system halts>
********************************************************************
<D. If the third or fifth of the six is chosen, boot into Ubuntu is successful>


I have tried the recommendation in B. to use 'chkdsk /r' in Windows. This took about 3 hours and had no effect on the error message. I also had made backups using "Back in time" which I tried (at least some of the directories) but none of these recovered directories had any noticeable effect on the error. This seems to be some basic device mounting problem that for some reason occurs only with the latest release and was triggered by some unknown event --- Why?? 

Help on isolating and correcting this problem would be greatly appreciated.

---

### Post by davidmohammed on 2010-09-05
try taking the mount of your ntfs partition out of the equation -

boot from live CD and edit your fstab...

get a command prompt. Then mount your Linux partition. Let's say that you have Linux installed on /dev/sda1 and that you are using ext4:

```
mkdir /virsto
mount -t ext4 /dev/sda1 /virsto

nano /virsto/etc/fstab
```

make the necessary changes to fstab and save it. 

```
umount /virsto
reboot
```

---

### Post by Lateralis on 2010-09-05
Curious.  

I *think* I have seen this before when Windows is put into a hibernate mode and then the computer booted into Linux.  I don't suppose that's what you did?  

It seems strange though that you can boot using the two other kernels but not the first; I'm using the 2.6.32-24-generic kernel.

---

### Post by virsto on 2010-09-05
Actually, this may have been what happened. That is, I thought that I did a graceful shut down from Windows; but, I was in hibernate mode --- this may very well have been what happened!

---

### Post by virsto on 2010-09-05
I am not sure that I follow what you are suggesting here. Sorry, but I will need to study this more --- I am not very knowledgeable in Linux commands. Perhaps you could expand a little more on your suggested fix.

--Thanks

---

### Post by virsto on 2010-09-05
> **davidmohammed said:**
> try taking the mount of your ntfs partition out of the equation -

boot from live CD and edit your fstab...

get a command prompt. Then mount your Linux partition. Let's say that you have Linux installed on /dev/sda1 and that you are using ext4:

```
mkdir /virsto
mount -t ext4 /dev/sda1 /virsto

nano /virsto/etc/fstab
```make the necessary changes to fstab and save it. 

```
umount /virsto
reboot
```

Thanks for looking at my problem. Could you please supply more details on your suggestions. I have attached two files that I extracted from "messages - System Log Viewer" that show all the messages that occurred for the last time that I was able to boot 32-24 (does not work now) and the other when I boot 32-23 (this does work). This might be useful. ;)

---

### Post by Lateralis on 2010-09-05
David is suggesting that Ubuntu is trying to automount the NTFS partition at startup, but some problem with that partition is causing Ubuntu to cease loading.  Whether a locked down or inaccessible NTFS partition would stop Ubuntu from booting or not I'm not sure - I don't suppose it should, but David's suggestion essentially is to remove the NTFS volume from the fstab file to see if it is the NTFS volume causing the error.    

To do this you will need to login to an Ubuntu distribution and edit the fstab file located in /etc.  If you can boot into Ubuntu using the 2.6.32-23 kernel then you may do that, or else boot from an Ubuntu live CD.  

If you do the former, simply edit /etc/fstab using whichever editor you like:

```

gksudo gedit /etc/fstab

OR

sudo nano /etc/fstab

```

What you will then need to do is comment out any line which looks like:
```

/dev/sdb1 /media/XP **ntfs-3g** defaults,locale=en_GB.UTF-8 0 0

```

Save the file and then try rebooting.  

If you do the latter you will need to mount the Ubuntu filesystem on your hard drive first before you can edit /etc/fstab.  David's post tells you how to do that.  

Hope this helps?

---

### Post by bcbc on 2010-09-05
I've seen this before. It has nothing to do with ntfs. It's the same problem others are having with the -24 kernel update, in that the initrd.img didn't build correctly. [http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

You should boot the -23 kernel and then run  ```
sudo update-initramfs &#8211;u -k 2.6.32-24-generic
```

(You get that extra ntfs message because you're running a wubi install)

---

### Post by virsto on 2010-09-05
> **bcbc said:**
> I've seen this before. It has nothing to do with ntfs. It's the same problem others are having with the -24 kernel update, in that the initrd.img didn't build correctly. [http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)

You should boot the -23 kernel and then run  ```
sudo update-initramfs –u -k 2.6.32-24-generic
```(You get that extra ntfs message because you're running a wubi install)

But when I execute your suggestion I get the following:

You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]    Specify kernel version or 'all'
 -c        Create a new initramfs
 -u        Update an existing initramfs
 -d        Remove an existing initramfs
 -t        Take over a custom initramfs with this one
 -b        Set alternate boot directory
 -v        Be verbose
 -h        This message

---

### Post by virsto on 2010-09-05
> **virsto said:**
> But when I execute your suggestion I get the following:

You must specify at least one of -c, -u, or -d.

Usage: /usr/sbin/update-initramfs [OPTION]...

Options:
 -k [version]    Specify kernel version or 'all'
 -c        Create a new initramfs
 -u        Update an existing initramfs
 -d        Remove an existing initramfs
 -t        Take over a custom initramfs with this one
 -b        Set alternate boot directory
 -v        Be verbose
 -h        This message

Ok, the mistake in your command was a double "-" before the u. I fixed this, executed the command which seemed to be ok --- no error being reported. Then rebooted and tried to run 32-24 --- the same error occurred during its attempted boot!

---

### Post by perspectoff on 2010-09-05
> **virsto said:**
> Actually, this may have been what happened. That is, I thought that I did a graceful shut down from Windows; but, I was in hibernate mode --- this may very well have been what happened!

Exactly right. This has happened to me, many, many, many times.

Hibernation mode of Windows has always been the problem, and I always see the errors you have posted.

---

### Post by virsto on 2010-09-05
> **Lateralis said:**
> David is suggesting that Ubuntu is trying to automount the NTFS partition at startup, but some problem with that partition is causing Ubuntu to cease loading.  Whether a locked down or inaccessible NTFS partition would stop Ubuntu from booting or not I'm not sure - I don't suppose it should, but David's suggestion essentially is to remove the NTFS volume from the fstab file to see if it is the NTFS volume causing the error.    

To do this you will need to login to an Ubuntu distribution and edit the fstab file located in /etc.  If you can boot into Ubuntu using the 2.6.32-23 kernel then you may do that, or else boot from an Ubuntu live CD.  

If you do the former, simply edit /etc/fstab using whichever editor you like:

```

gksudo gedit /etc/fstab

OR

sudo nano /etc/fstab

```What you will then need to do is comment out any line which looks like:
```

/dev/sdb1 /media/XP **ntfs-3g** defaults,locale=en_GB.UTF-8 0 0

```Save the file and then try rebooting.  

If you do the latter you will need to mount the Ubuntu filesystem on your hard drive first before you can edit /etc/fstab.  David's post tells you how to do that.  

Hope this helps?

Here is what is my fstab:

[B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0[/B]

---

### Post by virsto on 2010-09-05
> **perspectoff said:**
> Exactly right. This has happened to me, many, many, many times.

Hibernation mode of Windows has always been the problem, and I always see the errors you have posted.

Any suggestions on what to do next?

---

### Post by bcbc on 2010-09-05
Trying to mount a hibernated ntfs drive will give you a similar error, but this would happen all the time, not just with one particular kernel.

Second, you're not mounting the ntfs drive from /etc/fstab. Wubi installs always mount the windows host partitition before the virtual ubuntu disks can be mounted as part of the boot process.

Third, if you hibernate from windows, you won't get an option to boot a wubi install the next time you start your computer - it boots automatically into windows. 

I understand that you weren't able to fix your -24 kernel and initrd.img. But it doesn't mean that it's not the problem.  Just keep booting the -23 kernel until you can figure out a solution. Unless perhaps there's some feature with the -24 kernel you feel you can't live without?

---

### Post by virsto on 2010-09-05
A follow up after several responses to my initial posting on this strange problem.

This error in Ubuntu is my first instance of a "Windows related problem" in Ubuntu. I am still using Ubuntu 32-23, and will continue do do so, until this issue is resolved. However, it would be very nice to know the actual source of this problem, since there are different opinions on why this error occurs (see postings on this).

I was under the impression that Ubuntu was very safe from any problem  that occurred in Windows.  Is Ubuntu really vulnerable to Windows  related problems? It would be nice to know if it is possible to make Ubuntu completely independent of Windows related problems. I should also say that the error message posted in my original message is not very useful, and where is this error message stored? I could not find it in Ubuntu.

---

### Post by davidmohammed on 2010-09-05
Are you dual booting ubuntu and windows or are you using wubi?  If its the latter, that will explain your issues - especially if you allow windows to hibernate.

If you are using a true dual boot, then as suggested previously, the new kernel is causing your issue.  Keep booting into the .23 kernel.  Hopefully a new kernel release in the next month or two will resolve your problem.

---

### Post by bcbc on 2010-09-05
> **davidmohammed said:**
> Are you dual booting ubuntu and windows or are you using wubi?  If its the latter, that will explain your issues - especially if you allow windows to hibernate.

If you are using a true dual boot, then as suggested previously, the new kernel is causing your issue.  Keep booting into the .23 kernel.  Hopefully a new kernel release in the next month or two will resolve your problem.

How can you say: if you're using wubi then that is the problem, otherwise if you're not using wubi, then it's the kernel??? That doesn't make any sense. It's the same problem.

There is absolutely no issue hibernating windows when you have wubi. You just can't boot wubi after hibernating - and by 'can't' I mean 'you don't get the option', not 'it doesn't work'.

---

### Post by bcbc on 2010-09-05
> **virsto said:**
> A follow up after several responses to my initial posting on this strange problem.

This error in Ubuntu is my first instance of a "Windows related problem" in Ubuntu. I am still using Ubuntu 32-23, and will continue do do so, until this issue is resolved. However, it would be very nice to know the actual source of this problem, since there are different opinions on why this error occurs (see postings on this).

I was under the impression that Ubuntu was very safe from any problem  that occurred in Windows.  Is Ubuntu really vulnerable to Windows  related problems? It would be nice to know if it is possible to make Ubuntu completely independent of Windows related problems. I should also say that the error message posted in my original message is not very useful, and where is this error message stored? I could not find it in Ubuntu.

Let's ignore that this problem isn't windows related for an instance. Yes you can make ubuntu completely independent of Windows, by installing it to it's own partition. With Wubi you are running Ubuntu off a virtual disk that's stored on the windows file system.

---

### Post by davidmohammed on 2010-09-05
> **bcbc said:**
> How can you say: if you're using wubi then that is the problem, otherwise if you're not using wubi, then it's the kernel??? That doesn't make any sense. It's the same problem.

There is absolutely no issue hibernating windows when you have wubi. You just can't boot wubi after hibernating - and by 'can't' I mean 'you don't get the option', not 'it doesn't work'.

OK, understand what you are saying.  I suppose that still leaves the kernel .23 vs .24 release issue.  Hopefully a future release (or installing a newer kernel from mainline) will fix this issue.

---

### Post by virsto on 2010-09-06
I can now say that NONE of the suggestions solved my problem with 32-24. And trying different suggestions I actually caused the problem to propagate to 32-23 and 32-21, so I finally reached a state where I was unable to bootup any version of Ubuntu 10.04 and even worse could not bootup from a Ubuntu bootable CD that I had made. The message here is --- **don't try to get around this problem with 32-24 --- just live with it**.

I gave up early this morning and decided to start from scratch and install 10.04.1 (latest downloadable). This went rather smooth but there is still at least one problem -- I am unable to get my wireless network up and running (see my postings in Ubuntu forum --- Installation & Upgrades)

---

### Post by virsto on 2010-09-13
My solution:
1. Remove Ubuntu 10.04 completely
2. Downloaded **Ubuntu-10.04.1-desktop-amd64.iso** and burned a CD for it.
3. Bootup from  CD and followed instructions.

--V

---

