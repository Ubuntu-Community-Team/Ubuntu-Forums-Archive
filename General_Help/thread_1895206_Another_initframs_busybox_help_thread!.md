---
title: "Another initframs busybox help thread!"
date: 2011-12-14
forum: General Help
---

### Post by learst on 2011-12-14
Hi,

I've encountered the booting into busybox initramfs bug, the 2nd time after experiencing it the first time a few months ago. Both time were from ubuntu not being able to recover from the monitor sleep, where the screen lock display doesn't appear. I've been using ubuntu for almost 2 years now, still not knowing much, but frankly this is making me pull my hair out and thinking of switching from ubuntu. 

Anyway, the first time it happened, I followed the instructions found on this thread, which worked for me. 
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Note that the mounting problem was with sda5.

I tried repeating the same steps but failed.

```
sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        7310    58633362+   7  HPFS/NTFS
/dev/sda3            7310       19458    97574913    5  Extended
/dev/sda5            7310       18958    93561856   83  Linux
/dev/sda6           18958       19458     4012032   82  Linux swap / Solaris
``````
ubuntu@ubuntu:~$ sudo fsck -yv /dev/sda2
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2
```
```
ubuntu@ubuntu:~$ sudo debugfs -w /dev/sda2
debugfs 1.41.12 (17-May-2010)
/dev/sda2: Bad magic number in super-block while opening filesystem
```

I'm running Ubuntu on a Dell Inspiron 1420, with Nvidia GS 8400 M, and dual-boot with Windows Vista. 

Any help appreciated.

---

### Post by matt_symes on 2011-12-14
Hi

Why are you trying to fsck /dev.sda2 ? 

This is an NTFS partition and there is no fsck.ntfs for this filing system type. 
```

matthew@matthew-Aspire-7540:~/c_code$ ls /sbin/fsck* -l
-rwxr-xr-x 1 root root 30504 Aug  9 17:15 /sbin/fsck
-rwxr-xr-x 1 root root 13812 Aug  9 17:15 /sbin/fsck.cramfs
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext2 -> e2fsck
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext3 -> e2fsck
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext4 -> e2fsck
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext4dev -> e2fsck
-rwxr-xr-x 1 root root 26136 Aug  9 17:15 /sbin/fsck.minix
lrwxrwxrwx 1 root root     7 Aug 20 21:36 /sbin/fsck.msdos -> dosfsck
-rwxr-xr-x 1 root root   333 Dec 13 00:34 /sbin/fsck.nfs
lrwxrwxrwx 1 root root     7 Aug 20 21:36 /sbin/fsck.vfat -> dosfsck
matthew@matthew-Aspire-7540:~/c_code$ 
```

That is also the reason why debugfs will not work.

from man debugfs
> 
The debugfs program is an interactive file system debugger. It can be used to examine and change the state of an ext2, ext3, or ext4 file system.

You will need to use Windows if this partitions filing system needs to be checked.

Is your problem not with /dev/sda5 anyway ? Run fsck on that partition.

Kind regards

---

### Post by learst on 2011-12-14
> **matt_symes said:**
> Hi

Why are you trying to fsck /dev.sda2 ? 

This is an NTFS partition and there is no fsck.ntfs for this filing system type. 
```

matthew@matthew-Aspire-7540:~/c_code$ ls /sbin/fsck* -l
-rwxr-xr-x 1 root root 30504 Aug  9 17:15 /sbin/fsck
-rwxr-xr-x 1 root root 13812 Aug  9 17:15 /sbin/fsck.cramfs
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext2 -> e2fsck
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext3 -> e2fsck
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext4 -> e2fsck
lrwxrwxrwx 1 root root     6 Oct 25 03:21 /sbin/fsck.ext4dev -> e2fsck
-rwxr-xr-x 1 root root 26136 Aug  9 17:15 /sbin/fsck.minix
lrwxrwxrwx 1 root root     7 Aug 20 21:36 /sbin/fsck.msdos -> dosfsck
-rwxr-xr-x 1 root root   333 Dec 13 00:34 /sbin/fsck.nfs
lrwxrwxrwx 1 root root     7 Aug 20 21:36 /sbin/fsck.vfat -> dosfsck
matthew@matthew-Aspire-7540:~/c_code$ 
```That is also the reason why debugfs will not work.

from man debugfs


You will need to use Windows if this partitions filing system needs to be checked.

Is your problem not with /dev/sda5 anyway ? Run fsck on that partition.

Kind regards

Ok, I'm still a noob with a lot of stuff, beyond just exploring Ubuntu here and there. It's been quite a difficult transition for me to get used to Linux, switching from Windows.

> Why are you trying to fsck /dev.sda2 ? 
I was just repeating the steps from the thread I posted in my OP that worked for me the first time I encountered this busybox bug.

> You will need to use Windows if this partitions filing system needs to be checked.
I assume I just click on Check Disk in Windows to run this? Or are you suggesting another way?
> 
Is your problem not with /dev/sda5 anyway ? Run fsck on that partition.
The first time I had the busybox problem, it was with sda5. When I ran "sudo fdisk -l /dev/sda", the results displayed had the asterisk on sda5. This time the asterisk is on sda2. I assume that was the cause of the problem, hence I tried running debugfs.

Thanks again for all your help, and patience with the noob here.

---

### Post by matt_symes on 2011-12-14
Hi

> **learst said:**
> Ok, I'm still a noob with a lot of stuff, beyond just exploring Ubuntu here and there. It's been quite a difficult transition for me to get used to Linux, switching from Windows.

No worries. Sorry if i can accross a bit strong.

> 
I was just repeating the steps from the thread I posted in my OP that worked for me the first time I encountered this busybox bug.

Unfortunately, this will not apply this time. You need to tailor your fixes to the problem.

> 
I assume I just click on Check Disk in Windows to run this? Or are you suggesting another way?

Yes, i was suggesting chkdsk.

> 
The first time I had the busybox problem, it was with sda5. When I ran "sudo fdisk -l /dev/sda", the results displayed had the asterisk on sda5. This time the asterisk is on sda2. I assume that was the cause of the problem, hence I tried running debugfs.

The asterisk means it's a bootable partition. The asterisk bears no relation to your problem so you can discount it. 

Run fsck on the partition /dev/sda5 as it is that partition that contains your inittramfs and it is from there you are being dropped to the busy box prompt.

Kind regards

---

### Post by learst on 2011-12-14
> **matt_symes said:**
> 
Yes, i was suggesting chkdsk.

I left it running and gone to sleep. When I woke up, it was at the select OS screen, and strangely, the line/command for "select OS in 9 secs or default to Ubuntu" is gone.

Anyway, this didn't solve my problem.

> The asterisk means it's a bootable partition. The asterisk bears no relation to your problem so you can discount it. 

Run fsck on the partition /dev/sda5 as it is that partition that contains your inittramfs and it is from there you are being dropped to the busy box prompt.


Ok, thanks. But why does the bootable partition keeps changing? Previously it was sda5, and this time it is sda2.

Anyway, I repeated the same steps with debugfs on sda5 and it worked!! So now I'm a happy clam.

But I'm still quite disappointed to know that this is such a widespread problem. I've immediately disabled all suspend/hibernate and screensaver locking options on my laptop, and made a mental note not to do so.

Thanks again for your help.

---

### Post by matt_symes on 2011-12-15
Hi

> **learst said:**
> I left it running and gone to sleep. When I woke up, it was at the select OS screen, and strangely, the line/command for "select OS in 9 secs or default to Ubuntu" is gone.

Anyway, this didn't solve my problem.

I was really only suggesting chkdsk if you had problems with your Windows partition. My real advice was to run fsck on /dev/sda5.

> 
Ok, thanks. But why does the bootable partition keeps changing? Previously it was sda5, and this time it is sda2.Not sure why it should change. Grub does not need the bootable partition flag set though. Only Windows needs it if grub is not installed on your machine.

> 
Anyway, I repeated the same steps with debugfs on sda5 and it worked!! So now I'm a happy clam.Most of your grub stage 2 files will have been stored in your /dev/sda5 partition in the folder /boot. Grub stage 2 is what displays the grub menu. If it cannot read /boot, grub may hang.

> 
But I'm still quite disappointed to know that this is such a widespread problem. I've immediately disabled all suspend/hibernate and screensaver locking options on my laptop, and made a mental note not to do so.

Thanks again for your help.That would need further investigation to see why it's happening. Check in the log files to see if there is any information there.

Kind regards

---

