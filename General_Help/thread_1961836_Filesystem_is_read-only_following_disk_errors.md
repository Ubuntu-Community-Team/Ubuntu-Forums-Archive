---
title: "Filesystem is read-only following disk errors"
date: 2012-04-19
forum: General Help
---

### Post by sting14ray on 2012-04-19
I've been dual booting my system between Windows 7 and Ubuntu for a while now. A few days ago I upgraded my Linux to 11.10 and then yesterday I upgraded my Windows from the Home Premium edition to Ultimate. I forgot that I had hibernated my Linux side before I started upgrading Windows. After installing Windows I couldn't boot into Linux but I used Boot-Repair with the default options to fix it. I started Ubuntu, fsck ran while it was booting, and then I logged in. I tried to save some work but couldn't. I checked the properties for my filesystem and it said that that the owner was Root and my access was limited to read only. 

I ran fsck but it wouldn't run because it said the drive was mounted. 
I used the Ubuntu Live CD and fsck gave me errors about a bad super block and the magic number being wrong. I used mke2fs -n to look for the backup superblocks then tried to run fsck -b XXX (XXX = backup superblocks) and all of them gave the same error.

Going into the recovery console I ran "mount -o remount,rw -n / ", followed by "touch /forcefsck" and restarted into Ubuntu. Fsck would start to run then end immediately and nothing would change.

The computer is a 14 month old Dell laptop and has never given me any hard drive errors before. Disk Utility doesn't report any bad sectors and the overall assessment is the disk is healthy. I'm currently running the SMART Self-test and will post that when it finishes. I can copy files from my filesystem to an external hard drive and I'm not getting any errors while I do this so that's another reason I think the disk is fine, to be fair though I haven't tried to open the backups.

Output of "sudo fdisk -l":
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00182079

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400   de  Dell Utility
/dev/sda2          206848    30926847    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30926848   522605077   245839115    7  HPFS/NTFS/exFAT
/dev/sda4       522606590   976771071   227082241    5  Extended
/dev/sda5       958283776   976771071     9243648   82  Linux swap / Solaris
/dev/sda6       522606592   958283775   217838592   83  Linux

Partition table entries are not in disk order


sda1 (Dell Utility) is a 105 MB FAT partition.
sda2 (Recovery) is a 16GB NTFS Dell recovery partition.
sda3 (OS) is a 252 GB NTFS Windows 7 partition.
sda4 is a 233 GB extended partition for sda5 and sda6.
sda5 (Swap) is a 9.5 GB swap partition.
sda6 (/) is a 223 GB Ext4 Linux partition.


Output of "mount":
> /dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/szaheer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=szaheer)

Miscellaneous: Running Ubuntu 11.10, usually in the Xfce environment. Intel Core i3, 4 GB RAM, ATI Mobility Radeon 4650.

Any and all help will be greatly appreciated.

Thank you,
sting14ray

---

### Post by sting14ray on 2012-04-20
The SMART extended self-test just finished and I didn't get any errors.

---

### Post by sting14ray on 2012-04-20
Am I hosed? Should I just reformat it?

On a related note does anyone have experience with Dell's recovery partitions? Is it worth it to keep them? I've never used them before (which tells me something I guess) but am I missing something?

Thanks,
sting14ray

---

### Post by for.i.am.root on 2012-04-20
Looks like permission issues.

Try ls -l in the directory you are having problems with and it's parent directory. And post the results here.

---

### Post by sting14ray on 2012-04-20
Thank you very much. 

> szaheer@Sinspiron:/$ ls -l
total 144
drwxr-xr-x   2 root root  4096 2012-04-16 01:34 bin
drwxr-xr-x   3 root root  4096 2012-04-16 21:51 boot
drwxr-xr-x   2 root root  4096 2011-06-10 10:12 cdrom
-rw-r--r--   1 root root    48 2012-04-17 15:12 C:\nppdf32Log\debuglog.txt
drwxr-xr-x  16 root root  4220 2012-04-20 11:42 dev
drwxr-xr-x 165 root root 12288 2012-04-20 12:12 etc
drwxr-xr-x   3 root root  4096 2011-06-10 10:12 home
lrwxrwxrwx   1 root root    33 2012-04-16 08:22 initrd.img -> /boot/initrd.img-3.0.0-17-generic
lrwxrwxrwx   1 root root    33 2012-04-16 00:11 initrd.img.old -> boot/initrd.img-2.6.38-14-generic
drwxr-xr-x  21 root root 16384 2012-04-16 08:59 lib
drwxr-xr-x   4 root root 20480 2012-04-16 01:10 lib32
drwxr-xr-x   2 root root  4096 2012-04-16 08:31 lib64
drwx------   3 root root 16384 2011-06-10 10:06 lost+found
drwxr-xr-x   2 root root  4096 2012-04-20 11:42 media
drwxr-xr-x   2 root root  4096 2010-10-07 05:15 mnt
drwxr-xr-x   6 root root  4096 2011-10-10 21:19 opt
dr-xr-xr-x 177 root root     0 2012-04-20 07:41 proc
drwx------  16 root root  4096 2012-04-16 00:01 root
drwxr-xr-x  23 root root   880 2012-04-20 12:12 run
drwxr-xr-x   2 root root 12288 2012-04-16 01:37 sbin
drwxr-xr-x   2 root root  4096 2010-05-10 01:45 selinux
drwxr-xr-x   2 root root  4096 2010-10-07 11:56 srv
drwxr-xr-x  13 root root     0 2012-04-20 07:41 sys
drwxrwxrwt  14 root root 12288 2012-04-20 12:17 tmp
drwxr-xr-x  11 root root  4096 2012-04-16 00:56 usr
drwxr-xr-x  13 root root  4096 2012-04-20 02:33 var
lrwxrwxrwx   1 root root    29 2012-04-16 08:22 vmlinuz -> boot/vmlinuz-3.0.0-17-generic
lrwxrwxrwx   1 root root    30 2012-04-16 00:11 vmlinuz.old -> boot/vmlinuz-2.6.38-14-generic


---

### Post by for.i.am.root on 2012-04-20
You do not have ownership of your home directory or write access to anything.

sudo chown -R szaheer:szaheer /home/szaheer
sudo chmod -R 774? /home/szaheer

Quick and dirty :-D

The command would NOT include the ? mark. That is there because I *think* that would be the right permissions.

That will get it working, however, there are a lot of files that you may have issues with due to the permissions being wrong.

Anything else you need write access to you are going to have to change the ownership / permissions of.

---

### Post by sting14ray on 2012-04-20
Thanks a bunch, I'll go with this for now and if I still have trouble then I'll just reformat and reinstall everything.

---

