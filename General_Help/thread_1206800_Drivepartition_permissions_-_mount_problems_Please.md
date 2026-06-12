---
title: "Drive/partition permissions - mount problems: Please help"
date: 2009-07-07
forum: General Help
---

### Post by Dog walker on 2009-07-07
Hi,

I desperately need some help, but I'm new to Linux, particularly this problem and apologise in advance for asking for simple explanations, but PLEASE don't let this put everyone off of giving advice.

The problem is:- I wanted to automatically mount a particular drive partition on boot-up. I searched and read the forums and docs and couldn't understand some of the in-depth explanations, so I eventually went for (what I hoped was) the easy option and installed the 'Storage Device Manager' (PySDM) application.

I'm now getting problems such as... when trying to unmount a drives/partitions I get an error message saying 'can't unmount, volume seems to be mounted multiple times' and on other drives/partitions the error is 'only root can unmount volume'. (abbreviated error terms).

I'm sure if I keep on experimenting I will get to an unrecoverable situation, can someone please help me to put my drives/partitions back to normal, before I do make a big mistake.

Happy to supply any info and drive/partition details needed.

Many thanks for any help.
Ken.

---

### Post by michy99 on 2009-07-07
To start with, how about the output from these commands.```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> To start with, how about the output from these commands.```
sudo fdisk -l
df -h
cat /etc/fstab
```

Hi michy99, thanks for the reply.

Here is what I got (is that what was wanted?):-


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45134513

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       19456   105073132+   f  W95 Ext'd (LBA)
/dev/sda5            6376       11475    40965718+  83  Linux
/dev/sda6           11476       11985     4096543+  82  Linux swap / Solaris
/dev/sda7           11986       19456    60010776    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076cc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12158    97659103+   7  HPFS/NTFS
/dev/sdb2           12159       30401   146536897+   5  Extended
/dev/sdb5           12159       24316    97659103+  83  Linux
/dev/sdb6           24317       30401    48877731    7  HPFS/NTFS

Disk /dev/sdg: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d25b313

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4a50a96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001    7  HPFS/NTFS
ken@Data-Server:~$

---

### Post by michy99 on 2009-07-07
That is good for the first command, but I would like to see the result of the other two also.```
df -h
cat /etc/fstab
```
Also, how about this one.```
mount
```

---

### Post by Dog walker on 2009-07-07
Sorry I enterd the terminal commands all at once. Here is the rest:-

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4a50a96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001    7  HPFS/NTFS
ken@Data-Server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              39G  3.8G   33G  11% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  220K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  216K  502M   1% /dev
tmpfs                 502M  120K  502M   1% /dev/shm
lrm                   502M  2.2M  500M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb5              92G  1.4G   86G   2% /home
/dev/sdb6              49G   32G   18G  65% /media/sda1
/dev/sdb1              94G   92G  1.6G  99% /media/sdb1
/dev/sda1              49G   32G   18G  65% /media/sda1
/dev/sdg1             597G  573G   25G  96% /media/Data (ext-1)
/dev/sdh1             932G  142G  790G  16% /media/Data (ext-2)
ken@Data-Server:~$

ken@Data-Server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                           0  0  
# / was on /dev/sda5 during installation
UUID=46b8c6f0-cebb-446a-ba49-e4ae3b17ebc0  /               ext3         relatime,errors=remount-ro         0  1  
# /home was on /dev/sdb5 during installation
UUID=69c19d6b-5525-4d38-8cde-2ea084db22b5  /home           ext3         relatime                           0  2  
# swap was on /dev/sda6 during installation
UUID=b8974c8e-1fc9-42a7-907a-1b9447627d14  none            swap         sw                                 0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8              0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8           0  0  
/dev/sda7                                  /media/sda7     ntfs         nls=iso8859-1,ro,noauto,umask=000  0  0  
/dev/sdb6                                  /media/sda1     ntfs         defaults                           0  0  
/dev/sdb1                                  /media/sdb1     ntfs         defaults                           0  0  
/dev/sda1                                  /media/sda1     ntfs         defaults                           0  0  
ken@Data-Server:~$

---

### Post by Dog walker on 2009-07-07
ken@Data-Server:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb5 on /home type ext3 (rw,relatime)
/dev/sdb6 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ken/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ken)
/dev/sdg1 on /media/Data (ext-1) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh1 on /media/Data (ext-2) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ken@Data-Server:~$

---

### Post by Dog walker on 2009-07-07
Sorry for being untidy... I'm not too used to terminal yet.

---

### Post by michy99 on 2009-07-07
Ok, now we're getting somewhere. The first thing I see is that you have both /dev/sda1 and /dev/sda6 mounting to the same mountpoint, /media/sda1. That should be easy to fix. I need the output from another command:```
ls -la /media
```

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> Ok, now we're getting somewhere. The first thing I see is that you have both /dev/sda1 and /dev/sda6 mounting to the same mountpoint, /media/sda1. That should be easy to fix. I need the output from another command:```
ls -la /media
```


I'm so glad someone understands this... I'm totally lost! Thanks michy99, here it is:-


ken@Data-Server:~$ ls -la /media
total 52
drwxr-xr-x 11 root root 4096 2009-07-07 20:45 .
drwxr-xr-x 21 root root 4096 2009-06-28 05:16 ..
lrwxrwxrwx  1 root root    6 2009-06-28 02:36 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-06-28 02:36 cdrom0
drwxr-xr-x  2 root root 4096 2009-06-28 02:36 cdrom1
drwxrwxrwx  1 root root 8192 2009-06-24 18:39 Data (ext-1)
drwxrwxrwx  1 root root 4096 2009-07-02 00:10 Data (ext-2)
lrwxrwxrwx  1 root root    7 2009-06-28 02:36 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2009-06-28 02:36 floppy0
-rw-r--r--  1 root root  188 2009-07-07 20:45 .hal-mtab
-rw-------  1 root root    0 2009-07-07 20:45 .hal-mtab-lock
drwxrwxrwx  1 root root 4096 2009-07-01 04:57 sda1
drwxr-xr-x  2 root root 4096 2009-07-07 18:48 sda7
drwxrwxrwx  1 root root 4096 2009-07-07 00:27 sdb1
drwxr-xr-x  2 root root 4096 2009-07-07 18:56 sdb6
ken@Data-Server:~$

---

### Post by michy99 on 2009-07-07
First we will fix the sdb6 problem (I accidentally called it sda6 in the last post.) Open your fstab file for editing with this command:```
gksudo gedit /etc/fstab
```Find this line:```
dev/sdb6 /media/sda1 ntfs defaults 0 0 
```and change sda1 to sdb6, so it reads like this:```
dev/sdb6 /media/sdb6 ntfs defaults 0 0 
```Save the file and close the editor.

Then run this command and see if you get any errors:```
sudo mount -a
```

---

### Post by rbc on 2009-07-07
Not trying to highjack the thread, but michy99, if you could explain something when you finish getting the OP straightened out.

/dev/sdg1 on /media/Data (ext-1) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh1 on /media/Data (ext-2) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

To the untrained eye, these appear to also have the same mountpoint, or does the (ext-1) and (ext-2) effectively make them two different mountpoints. Just curious as I have never seen those terms before

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> First we will fix the sdb6 problem (I accidentally called it sda6 in the last post.) Open your fstab file for editing with this command:```
gksudo gedit /etc/fstab
```Find this line:```
dev/sdb6 /media/sda1 ntfs defaults 0 0 
```and change sda1 to sdb6, so it reads like this:```
dev/sdb6 /media/sdb6 ntfs defaults 0 0 
```Save the file and close the editor.

Then run this command and see if you get any errors:```
sudo mount -a
```

Done: the final command produced nothing (back to the prompt).

---

### Post by michy99 on 2009-07-07
Ok, how about rebooting the computer and see if the drives are mounted as you would expect them to be.

---

### Post by michy99 on 2009-07-07
> **rbc said:**
> Not trying to highjack the thread, but michy99, if you could explain something when you finish getting the OP straightened out.

/dev/sdg1 on /media/Data (ext-1) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdh1 on /media/Data (ext-2) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

To the untrained eye, these appear to also have the same mountpoint, or does the (ext-1) and (ext-2) effectively make them two different mountpoints. Just curious as I have never seen those terms before

I believe that this is a two disk RAID, which appears to the file system as a single disk. If that is wrong, someone can correct me.

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> Ok, how about rebooting the computer and see if the drives are mounted as you would expect them to be.


Re-booted.

I have 5 drives/partitions automatically mounting. The 2 external USB drives will unmount properly, but I can't unmounte the other 3. Messages I'm getting are:

1. only root can unmount/dev/sda1 from /media/sda1

2. only root can unmount/dev/sdb6 from /media/sdb6

3. only root can unmount/dev/sdb1 from /media/sdb1

---

### Post by Dog walker on 2009-07-07
Oh just discovered too that it won't let me mount the other internal partiton... says I don't have the priviledges.

---

### Post by michy99 on 2009-07-07
> **Dog walker said:**
> Re-booted.

I have 5 drives/partitions automatically mounting. The 2 external USB drives will unmount properly, but I can't unmounte the other 3. Messages I'm getting are:

1. only root can unmount/dev/sda1 from /media/sda1

2. only root can unmount/dev/sdb6 from /media/sdb6

3. only root can unmount/dev/sdb1 from /media/sdb1

That is normal. Usually you don't need to unmount internal drives. When you do need to, you use sudo. For example:```
sudo umount /media/sda1
```

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> That is normal. Usually you don't need to unmount internal drives. When you do need to, you use sudo. For example:```
sudo umount /media/sda1
```

I'm sure you right michy99, but the internals were not automatically mounted prior to my messing around and I could mount/unmount them successfully.

I just tried the terminal option to unmount and yes it works, but if I try to remount it says I don't have the priviledges again.

I like to keep some drives unmounted, because I share the box and don't really want drives/partitions getting messed up or accidently interfered with.

Do you know of a way to get back to original, without a re-install.

---

### Post by michy99 on 2009-07-07
If you don't want them to automount, then remove the lines referring to those partitions in the fstab file. Just open it for editing like you did before. Instead of removing the lines, you can put a # at the beginning of a line and it will be ignored. That way you can easily add it back if you want to.

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> If you don't want them to automount, then remove the lines referring to those partitions in the fstab file. Just open it for editing like you did before. Instead of removing the lines, you can put a # at the beginning of a line and it will be ignored. That way you can easily add it back if you want to.

Will that also give me back the privileges to manually mount and unmount them?

---

### Post by michy99 on 2009-07-07
You should be able to mount them by clicking on them in the Places menu, and unmount them by right-clicking on the desktop or the filebrowser.

---

### Post by Dog walker on 2009-07-07
> **michy99 said:**
> You should be able to mount them by clicking on them in the Places menu, and unmount them by right-clicking on the desktop or the filebrowser.

michy99, thank you very VERY much.

I'm in the middle of backing up the drives from my Win boot and will give it all another try when this is finished (a few hours!). Will post if I'm stuck.

Thanks again and good wishes.
Ken.

---

### Post by amitkr on 2009-07-09
> **michy99 said:**
> You should be able to mount them by clicking on them in the Places menu, and unmount them by right-clicking on the desktop or the filebrowser.

booting problem, not able to login.

It starts with a black screen saying:

/etc/init.d/rc: 2: sed: Permission denied (several times)

with command- sudo fdisk -l, I found my partition of linux as sda5

not able to mount with the following command:

sudo mount /dev/sda5/home/amit

Plz help me to recover from this as my data is at stake. I am able to view my folders by ls command but not able to login. plzzzzzzzz i am anew user of ubuntu. :confused:

---

