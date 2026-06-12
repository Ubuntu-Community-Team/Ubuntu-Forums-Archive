---
title: "portable hard drive read-only filesystem"
date: 2011-06-27
forum: General Help
---

### Post by evilbrent on 2011-06-27
I have a portable hard drive which works fine on my work windows 7 computer.

I just did a completely clean install of xubuntu 10.04 on a 3rd computer and the drive worked fine for about 30 seconds - I was able to write a file to the drive in that time. Now the entire drive is read-only.  

Note - the files and folders themselves give read-write access but it's the filesystem which is marked as read-only. 

Can someone tell me what's going on? It's not a hardware issue (works on windows), it's not a software issue (same behaviour on entirely new linux). It must be some setting on the drive itself yes?

Can anyone help me to trick linux into thinking it can permanently write to this drive?

---

### Post by buchs on 2011-06-27
Would you post the contents of two files:
   /etc/fstab
   /etc/mtab
grabbing them (1) as it is now (read-only) and then (2) immediately after a fresh reboot and (after reboot is complete) reattachment of the drive.

---

### Post by evilbrent on 2011-06-27
Drive not showing up in Nautilus in new computer right now. This is the fstab and mstab from this computer.

proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73  none         swap  sw                            0  0  
UUID=d4278f40-2c1b-4cb5-82ef-0948deec2af5  /            ext4  errors=remount-ro,user_xattr  0  1  
/dev/sdb1                                  /media/sdb1  vfat  users,user                    0  0


/dev/sda1 / ext4 rw,errors=remount-ro,user_xattr 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/brent/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=brent 0 0
/dev/sdb1 /media/sdb1 vfat rw,noexec,nosuid,nodev,user=brent 0 0





I've recently restarted this computer so I was able to write a new text file to the drive and then edit it and save it. I navigated around the drive for a bit then went back to the file and was unable to save changes to the file - system was saying "read-only filesystem".

fstab and mtab are now.

proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73  none         swap  sw                            0  0  
UUID=d4278f40-2c1b-4cb5-82ef-0948deec2af5  /            ext4  errors=remount-ro,user_xattr  0  1  
/dev/sdb1                                  /media/sdb1  vfat  users,user                    0  0

/dev/sda1 / ext4 rw,errors=remount-ro,user_xattr 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/brent/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=brent 0 0
/dev/sdb1 /media/sdb1 vfat rw,noexec,nosuid,nodev,user=brent 0 0




They look the same to me.

---

### Post by evilbrent on 2011-06-27
Apologies - I rebooted my computer completely. This is the FSTAB and MTAB fresh from reboot:

proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
UUID=cc7b51e8-18e0-4d07-9268-c5538a2abf73  none         swap  sw                            0  0  
UUID=d4278f40-2c1b-4cb5-82ef-0948deec2af5  /            ext4  errors=remount-ro,user_xattr  0  1  
/dev/sdb1                                  /media/sdb1  vfat  users,user                    0  0

/dev/sda1 / ext4 rw,errors=remount-ro,user_xattr 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb1 /media/sdb1 vfat rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/brent/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=brent 0 0




Althouth I note that it's now saying that root is the owner.

---

### Post by evilbrent on 2011-06-27
also - ls -la of the drive gives

brent@Bertha:/media/sdb1$ ls -la
total 1412
drwxr-xr-x 10 root  root   16384 1970-01-01 10:00 .
drwxr-xr-x  4 brent root    4096 2011-06-27 21:29 ..
drwxr-xr-x  3 root  root   16384 2011-05-15 23:13 bvnvbn
drwxr-xr-x  3 root  root   16384 2011-05-25 13:18 jghvgv]
drwxr-xr-x 18 root  root   16384 2011-05-08 21:49 movies
drwxr-xr-x 10 root  root   16384 2011-05-08 20:44 my documents
-rwxr-xr-x  1 root  root       0 2011-06-08 14:34 New Empty File
-rwxr-xr-x  1 root  root      20 2011-06-27 23:36 new file
drwxr-xr-x  3 root  root   16384 2010-09-09 08:24 $RECYCLE.BIN
drwxr-xr-x  2 root  root   16384 2010-08-17 19:42 Recycled
drwxr-xr-x  3 root  root   16384 2010-08-17 19:42 System Volume Information
drwxr-xr-x  5 root  root   16384 2010-10-07 20:40 .Trash-1000
-rwxr-xr-x  1 root  root 1269438 2010-08-21 12:52 untitled.bmp

---

### Post by evilbrent on 2011-06-27
Doing chmod says it's read only.

brent@Bertha:/media/sdb1$ chmod 777 /media/sdb1
chmod: changing permissions of `/media/sdb1': Read-only file system


Doing chown says it's read-only.

brent@Bertha:/media/sdb1$ sudo chown -R brent /media/sdb1
[sudo] password for brent: 
chown: changing ownership of `/media/sdb1/.Trash-1000/info/Batman The Dark Knight [2008] dvd rip nlx.trashinfo': Read-only file system

etc etc etc for every file in the drive.

---

### Post by buchs on 2011-06-28
I assume the drive is sdb1, accessed through the mount point of /media/sdb1. The first thing I would do is comment-out the line in /etc/fstab mentioning sdb1 (with addition of a leading #). This will, I believe, allow the automounter mount the drive. 

You might also check the message log for mentions of sdb1:
```
dmesg|grep sdb1|tail -100
```
You can post that output here and we can see if anything triggers off of that. I would suggest you boot the system without the portable drive inserted. Then after the system is settled (based on your boot time, probably > 1 minute), insert the drive. Wait about 20 seconds (and don't access the drive) and run the above command. You could further see if you get it to change to read-only and run the same command. 

I recently had a problem using USB Flash drives on a fresh install of Ubuntu 11.04. Commenting out the line in /etc/fstab fixed that.

---

### Post by evilbrent on 2011-06-30
Hi, thanks for replying. Ok, I think I may have something useful.

When I reboot the computer and plug the drive, named x, in and waited I got 

> brent@Bertha:~$ dmesg|grep sdb1|tail -100
[  308.061149]  sdb: sdb1


Everything looks good. I can open a text file in /media/x and edit it. Save it. Edit and save it again. Waited. Edit and save again. Ok.

Then in Nautilus I double click on the folder /media/x/movies and back to /media/x and I see a padlock icon on movies now and there is an error message:

> brent@Bertha:~$ dmesg|grep sdb1|tail -100
[  308.061149]  sdb: sdb1
[  591.020613] FAT: Filesystem error (dev sdb1)

...and now I've checked the errors again 3 minutes later without touching the drive and I've got more errors:

> brent@Bertha:~$ dmesg|grep sdb1|tail -100
[  308.061149]  sdb: sdb1
[  591.020613] FAT: Filesystem error (dev sdb1)
[  646.894160] FAT: Filesystem error (dev sdb1)
[  654.393726] FAT: Filesystem error (dev sdb1)

I can still read from the drive. Just not write. Something is definitely screwy. Any ideas?

----

As for editing out the /dev/sdb1 line in fstab - that appears to have done some good. Since I've been having this problem I've been seeing random /sdb1 drives mounted on the left of Nautilus, but that's all looking much neater now I just see "1.0TB Hard Disk: x". But the drive is still read-only filesystem.

---

### Post by buchs on 2011-06-30
Next, I would try a file system check. You can run that on Windows or Linux. On Windows, the command line tool depends upon your version. Generally you can right-click on the drive icon in Windows Explorer, choose Properties and then Tools. At least, I think that is correct, but haven't done it in a while.

On Linux, here are the steps I would follow. Make sure you have a backup of any critical data, just in case. The drive should be unmounted: sudo umount /dev/sdb. Then run: sudo fsck -t msdos /dev/sdb. There may be useful diagnostic output. You can check the return status by immediately following it with: echo $? (in bash). You can compare that status with the table in the manual page for fsck (man fsck). 

Probably the safest way to go is to do the check on Windows first, if you have not done that for a while. Windows these days will run a check after some long period of time, if the drive is attached on boot-up. When going to Linux for the check, you have the, I suppose slight, chance that there is something that Linux thinks is wrong with the file system, but Windows is ok with it, yet when Linux fixes it, Windows is unhappy. Hence, having the backup is the safest. 

I think that fsck fixes simple problems automatically, but it will tell you your options with more complex problems. You can also run it in a simulate mode or tell it not to fix automatically. See the man page for these options.

---

### Post by evilbrent on 2011-07-01
Win!!

Using the chkdsk in windows fixed the drive!!

Thanks heaps - I was just about ready to go out and replace it. Cheers. :)

25 internets for you :D:D

---

