---
title: "Stuck at startup"
date: 2009-12-12
forum: General Help
---

### Post by 7raTEYdCql on 2009-12-12
I use Ubuntu 9.10. Recently, I haven't been able to boot into my machine.

Pressing f1, then places me on a shell screen which shows me the following error.
> 
Gave up waiting for the root device. Common problems:
-Boot args(cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Chech root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dv)

ALERT! /dev/disk/by-uuid/----big-no---- does not exist. Dropping to a shell.

BusyBox v 1.13.3 (Ubuntu ...) built in shell ash.

(initramfs):



Upon listing in the initramfs prompt, the standard root folders weren't present. As far as i can recollect the following were the folders.
/dev
/bin
/proc
/cat
/lib and a few more. There was no /boot.

Can someone please help.

---

### Post by Vishnu V on 2009-12-12
Can you post the output of 
```

sudo blkid
cat /proc/cmdline

```
I don't know  these commands work from (initramfs)
if not please do it from a live cd

---

### Post by 7raTEYdCql on 2009-12-13
In initramfs sudo is invalid. So a plain run of blkid returned the following
> 
(initramfs) blkid
/dev/sda1: UUID="---" LABEL="System Reserved" TYPE="ntfs"
/dev/sda2: UUID="---" TYPE="ntfs"
/dev/sda3: UUID="---" TYPE="swap"

(initramfs) cat /proc/cmdline
BOOT_IMG=/boot/vmlinuz... root=UUID="---" ro quiet splash

Someone please help.

Is there a simpler way of saving the output of an initramfs session, to a file, on my disk. Something like a printscreen in terminal.

---

### Post by 7raTEYdCql on 2009-12-13
Now this is weird, i booted into a live cd, and my original ubuntu partition is simply not detected. I earlier had two primary partitions, Ubuntu and Windows, the ext4 ubuntu partition is not detected any more. Can someone please help.

---

### Post by 7raTEYdCql on 2009-12-13
This is the output of your above commands on a live cd.
> 
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A68ACB838ACB4F0D" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="1250D4F250D4DE13" TYPE="ntfs" 
/dev/sda3: UUID="f2e31ba7-fa84-4039-ae25-ed17928d3038" TYPE="swap" 
/dev/sdb1: LABEL="Mehrzad" UUID="FD5E-80DB" TYPE="vfat" 
ubuntu@ubuntu:~$ cat /proc/cmdline
initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
ubuntu@ubuntu:~$ 


---

### Post by cpttripzz on 2009-12-14
I had the same issue. I fixed this issue by chrooting into the old root directory

see this article [http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

and then running sudo apt-get update; sudo apt-get dist-upgrade

Hope this helps everybody else with this problem.

---

### Post by 7raTEYdCql on 2009-12-15
> **cpttripzz said:**
> I had the same issue. I fixed this issue by chrooting into the old root directory


But my old root-partition isn't detected. So how does the above work??

---

### Post by 7raTEYdCql on 2009-12-18
On an ubuntu live cd, sudo chroot mounpoint /bin/bash doesn't seem to work. I get the error /bin/bash not found.

Can someone please help.

---

