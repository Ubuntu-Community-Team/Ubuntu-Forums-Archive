---
title: "No init found mounting boots into busy box"
date: 2010-11-29
forum: General Help
---

### Post by claven123 on 2010-11-29
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)


I may have shut down the computer in error.  I had the Live USB thumb drive in and booted to the live ubuntu and I went to shut it down and it hung up and wouldn't shut down.  I went to the terminal and did shutdown now and it went to shutdown and hung I had to do a hard shut down.

The next day I booted and go the above message.  I did some searching and found some possible solutions.  One was to load the liver ubuntu and unmount the partition.  I did this and my swap file has a key next to it, indicating it is mounted.  Along with the parent extended partition. I went to  unmount and that option is greyed out.  I then went to do the swapoff option, then gparted hangs.  When I close the gparted and restart it shows them as unmounted.  When I reboot same error.  However, it will not shut down from the live ubuntu, it hangs.

I can do a clean install, since this is a reasonably new laptop that I dual boot with windows XP.  I can still use and run windows, so the drive is 'ok' at least the windows partition.  I am using ubuntu 10.10 and it ran without issues until now.

I think that grub2 is corrupt and the other solution was to reinstall this.  So that is the next option, if not I can do a clean install. However, to do this I have to turn off the swap and that is not working at this time, or at least I think.

Any ideas?

---

### Post by claven123 on 2010-11-29
Fdisk output....


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316       18608   138894426    7  HPFS/NTFS
/dev/sda4           18608       38914   163108865    5  Extended
/dev/sda5           38085       38914     6660096   82  Linux swap / Solaris
/dev/sda6           18608       38085   156448768   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cdc33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          51       49600     3963968    b  W95 FAT32
ubuntu@ubuntu:~$ 



ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ 



Any ideas?

---

### Post by drs305 on 2010-11-29
The first thing to try is to run the following from the LiveCD with sda6 unmounted. It will attempt to fix any errors induced during the unintended shutdown:

```
sudo umount /dev/sda6 # just to be sure it's umounted
sudo e2fsck -f -y -v /dev/sda6
```

You can also run a simlar check from within Gparted if you are more comfortable doing it that way.

Once you have run the check(s), reboot and see if it boots.

If not, it may help to run the boot info script from the LiveCD Desktop and post the contents of the RESULTS.txt file it creates. You can get the script and instructions from:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by claven123 on 2010-11-29
Do I need to do this on sda6, when sda5 is the swap file and sda4 are mounted.  I attempted to do a manual unmount with umount command, it stated that they are not mounted.

Thanks for the help.

Dennis

---

### Post by claven123 on 2010-11-29
Screen shot of gparted.

---

### Post by drs305 on 2010-11-29
> **claven123 said:**
> Do I need to do this on sda6, when sda5 is the swap file and sda4 are mounted.  I attempted to do a manual unmount with umount command, it stated that they are not mounted.

Thanks for the help.

Dennis

I just gave you the unmount command for sda6 in case you had previously mounted it to look at the contents. On an initial boot to the LiveCD the ubuntu partition would not be mounted. It's okay if the extended or swap are mounted, although I try to unmount anything I can before running fsck operations. You should be able to turn off swap by highlighting the swap partition and then selecting "Partition, Swapoff" - but it's not necessary.

---

### Post by claven123 on 2010-11-29
BTW, the partition swap off does not really work, it never completes, just keeps going and going.

I'm running the bash command now for the boot info script and it's still running and running checking sda6....

Not sure what's going on.

Thanks,

Dennis

---

### Post by drs305 on 2010-11-29
> **claven123 said:**
> BTW, the partition swap off does not really work, it never completes, just keeps going and going.

I'm running the bash command now for the boot info script and it's still running and running checking sda6....

Not sure what's going on.

Thanks,

Dennis

The script normally completes within a minute. If it's taking a long time and you haven't performed the fsck check, just abort it and try it after running e2fsck.

---

### Post by claven123 on 2010-11-29
here is the output from the scan....

```
   ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
/dev/sda5 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck -f -y -v /dev/sda5
fsck from util-linux-ng 2.17.2
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda4
e2fsck 1.41.12 (17-May-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?
ubuntu@ubuntu:~$ 
                
```


Note, I did the swap off and had to manually shutdown gparted to get out.  I was not able to do the scan.

Thanks

---

### Post by drs305 on 2010-11-29
The check is to be done on your Ubuntu partition, sda**6**

---

### Post by claven123 on 2010-11-29
Did that also... sorry didn't get posted the last time....

```
    ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda6
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 
         
```

Not sure what to do next....

Dennis

---

### Post by claven123 on 2010-11-29
umount shows it as not mounted.


Will a clean install help?  Or, do I have to reinstall grub2?



Dennis

---

### Post by drs305 on 2010-11-29
A clean install will most likely fix things. I would boot into Windows and delete the Ubuntu and swap partitions. Do you have any data you need to retrieve from Ubuntu. There may be other steps we could try, such as reinstalling G2 but the chances of that working are slight.

One more thing you can try: Do you access your Ubuntu partition via Windows (using ext2fs or something similar)? It's possible that Windows has rendered the other partitions unusable. You might try booting into Windows and shutting down normally.

---

### Post by claven123 on 2010-11-29
Well, I just went in and turned of the swap, which never ended.  I then deleted the partition... which gave an error that it didn't work....  then when I reloaded gparted it was unallocated.  I then went to re install ubuntu and I don't have an internet connection, so will have to complete when I get to a LAN line.

I did have a dual boot and yes, I was able to get into windows and use it.  I had access via the grub loader menu at boot up.

When I boot now I get the error no partition..... as expected.

I did not delete the swap, but I guess I can also.

Seems something was not right.... oh well.  

One other odd thing, while in the USB live ubuntu I kept getting low storage errors.... not sure why, I have a 4gb USB drive only 50% full.

Will post more later tonight.

Thanks for all your help.

---

### Post by claven123 on 2010-11-30
Well, I reinstalled ubuntu 10.10, and so far all is well.  Quite the time...  I had to delete the swap partition, since it wouldn't install until I did so.  Apparently the swap file was involved in the problem.  Not sure why, but it works so far.

Thanks for all the help, I learned a bit more on my linux journey.

---

### Post by Jimmy9pints on 2011-01-14
Thanks for writing updates. Very helpful.

---

