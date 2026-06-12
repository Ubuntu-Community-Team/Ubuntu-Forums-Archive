---
title: "Cannot see hidden folders on DVD"
date: 2011-08-29
forum: General Help
---

### Post by bob-linux-user on 2011-08-29
I am running Ubuntu 11.04. On Nautilus I have the "Show hidden and backup files ticked" I have a DVD Rom that came with a magazine (Computer Shopper Issue 284, a magazine based in the UK ) 

When I display the DVD in Nautilus I can only see three files (not folders). When I reboot in Windows XP I can see many folders and go into them and see sub folders and files etc. All these folders show up in XP as being "faint" and I see from their attributes they are hidden. 

How can I make Nautilus see these folders please?
(It is the same for Thunar and Konquerer as well.)

---

### Post by Slim Odds on 2011-08-29
> **bob-linux-user said:**
> I am running Ubuntu 11.04. On Nautilus I have the "Show hidden and backup files ticked" I have a DVD Rom that came with a magazine (Computer Shopper Issue 284, a magazine based in the UK ) 

When I display the DVD in Nautilus I can only see three files (not folders). When I reboot in Windows XP I can see many folders and go into them and see sub folders and files etc. All these folders show up in XP as being "faint" and I see from their attributes they are hidden. 

How can I make Nautilus see these folders please?
(It is the same for Thunar and Konquerer as well.)

Please show us what the files look like in XP.

---

### Post by bob-linux-user on 2011-08-29
Here it is.Please see snapshot attached.Thanks.

---

### Post by sbraz on 2011-08-29
**ctrl+h** ? :)

---

### Post by bob-linux-user on 2011-08-29
No that was the first thing I tried.

---

### Post by sbraz on 2011-08-29
> **bob-linux-user said:**
> No that was the first thing I tried.
my bad, i didn't read your post correctly. :)

i have no idea, maybe there's some DRM bug involved? :confused:

---

### Post by Slim Odds on 2011-08-29
With the DVD mounted, what does the mount command say the image type is?

There is no reason those directories shouldn't show....

That hidden attribute is meaningless in linux.

---

### Post by bob-linux-user on 2011-08-30
Hello Slim. Thanks.

I am not a command line wizard. What exactly should I type in terminal when I get back to my computer later this evening?

regards

Bob

---

### Post by Slim Odds on 2011-08-30
> **bob-linux-user said:**
> Hello Slim. Thanks.

I am not a command line wizard. What exactly should I type in terminal when I get back to my computer later this evening?

regards

Bob

I should have been more clear when I said "mount command".

Open a Terminal after you get the DVD mounted.

```
mount
```See what it says...

You can also use:
```
df -T
```Which shows the file system type for each mount point.

---

### Post by bob-linux-user on 2011-08-30
[SIZE="2"][SIZE="1"]Thanks Slim
Here goes:-
~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/deskpc1/.Private on /home/deskpc1 type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=***********************
gvfs-fuse-daemon on /home/deskpc1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deskpc1)
/dev/sr1 on /media/DPCS1011DVD type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)

~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda2     ext4    71637352  44193668  23804644  65% /
none      devtmpfs     1016124       696   1015428   1% /dev
none         tmpfs     1025384       188   1025196   1% /dev/shm
none         tmpfs     1025384       212   1025172   1% /var/run
none         tmpfs     1025384         0   1025384   0% /var/lock
/dev/sda1  fuseblk    77593596  17137896  60455700  23% /media/sda1
/home/deskpc1/.Private
          ecryptfs    71637352  44193668  23804644  65% /home/deskpc1
/dev/sr1       udf     4407534   4407534         0 100% /media/DPCS1011DVD[/SIZE][/SIZE]

---

### Post by Slim Odds on 2011-08-30
> **bob-linux-user said:**
> [SIZE=2][SIZE=1]Thanks Slim
Here goes:-
~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/deskpc1/.Private on /home/deskpc1 type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=***********************
gvfs-fuse-daemon on /home/deskpc1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deskpc1)
/dev/sr1 on /media/DPCS1011DVD type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)

~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda2     ext4    71637352  44193668  23804644  65% /
none      devtmpfs     1016124       696   1015428   1% /dev
none         tmpfs     1025384       188   1025196   1% /dev/shm
none         tmpfs     1025384       212   1025172   1% /var/run
none         tmpfs     1025384         0   1025384   0% /var/lock
/dev/sda1  fuseblk    77593596  17137896  60455700  23% /media/sda1
/home/deskpc1/.Private
          ecryptfs    71637352  44193668  23804644  65% /home/deskpc1
/dev/sr1       udf     4407534   4407534         0 100% /media/DPCS1011DVD[/SIZE][/SIZE]


Ok, so it's a UDF disk. That's pretty standard for a DVD.

See if you can find out which version of UDF it uses.

Try the program "dvd+rw-mediainfo"

I've never used it before, but it looks like it might shed some light.

Still don't really have clue why you'd have issues. As are as I know, linux should support UDF just fine.

---

### Post by bob-linux-user on 2011-08-30
Here is results 
~$ dvd+rw-mediainfo /dev/dvd
INQUIRY:                [TSSTcorp][CDDVDW SH-S202H ][SB00]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         10h, DVD-ROM
GET [CURRENT] PERFORMANCE:
 Write Performance:     20.0x1385=27700KB/s@[0 -> 2204719]
 Speed Descriptor#0:    08/2298496 R@16.0x1385=22160KB/s W@20.0x1385=27700KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2204720*2KB=4515266560
DVD-ROM media detected, exiting...
deskpc1@deskpc1:~$ 

I have also tried the dvd in another computer.Exactly the same.

---

### Post by bob-linux-user on 2011-08-31
I have reported it on launchpad as a bug

---

