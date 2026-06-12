---
title: "cp -rfp fails. &quot;No space left on device&quot; error"
date: 2011-01-19
forum: General Help
---

### Post by anilp on 2011-01-19
I was running a python script tool and got this error.
Exception: Command cp -Rfp /home/anil/mydroid/myfs/* /tmp/tmpX2KZDc
failed

(I am on dual boot ubuntu 10.10 with Win XP.)

Here is a partial output from the console. Note the "No space left on device" error, when writing to /tmp.
---
> mke2fs 1.41.12 (17-May-2010)
Filesystem label=android_fs
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
64000 inodes, 256000 blocks
12800 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67371008
32 block groups
8192 blocks per group, 8192 fragments per group
2000 inodes per group
Superblock backups stored on blocks: 
        8193, 24577, 40961, 57345, 73729, 204801, 221185

Writing inode tables: done                            
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 22 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
cp: writing `/tmp/tmpX2KZDc/system.image': No space left on device
---

Tried to find if my filesystem was full - is not full.

> anil@anil-HP-EliteBook-8440p:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda5            3637248  956625 2680623   27% /
none                  212289     867  211422    1% /dev
none                  215088       6  215082    1% /dev/shm
none                  215088      49  215039    1% /var/run
none                  215088       1  215087    1% /var/lock
/dev/sr0                   0       0       0    -  /media/GParted-live
anil@anil-HP-EliteBook-8440p:~$ 
---------
anil@anil-HP-EliteBook-8440p:~$ **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              55G   37G   16G  70% /
none                  1.5G  320K  1.5G   1% /dev
none                  1.5G  1.7M  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sr0              115M  115M     0 100% /media/GParted-live
anil@anil-HP-EliteBook-8440p:~$ 
---------
anil@anil-HP-EliteBook-8440p:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             57265436  38048008  16308500  70% /
none                   1501708       320   1501388   1% /dev
none                   1507304      2624   1504680   1% /dev/shm
none                   1507304        88   1507216   1% /var/run
none                   1507304         0   1507304   0% /var/lock
/dev/sr0                116834    116834         0 100% /media/GParted-live
anil@anil-HP-EliteBook-8440p:~$ 
--------
anil@anil-HP-EliteBook-8440p:~$ sudo du -hc --max-depth=1
2.4M	./.cache
104K	./.gconfd
24K	./.gnash
148K	./.pulse
1.9M	./.netx
4.0K	./Music
4.0K	./Public
104K	./Pictures
4.0K	./.gnome2_private
4.0K	./.InstallAnywhere
8.0K	./Desktop
8.0G	./mydroid
7.9G	./mydroid-google-src
144K	./.compiz
24K	./.gnupg
116K	./.gnome2
136K	./.config
12K	./.mission-control
du: cannot access `./.gvfs': Permission denied
12K	./hello
221M	./backup
214M	./Code drop 12-21
4.0K	./Templates
4.0K	./.nautilus
532K	./.local
8.1G	./mydroid-okl-12-21-2010
44K	./.pki
20K	./.repoconfig
7.0M	./Documents
2.7G	./secure_12-21-2010b
1.4G	./bin
732K	./.thumbnails
12K	./.dbus
340K	./.gstreamer-0.10
17M	./.evolution
1.2M	./astyle
36K	./.subversion
64K	./.fontconfig
4.0K	./Videos
24K	./.android
774M	./Downloads
908K	./.gconf
4.0K	./.hplip
1.9M	./.openoffice.org
614M	./CodeSourcery
101M	./.mozilla
87M	./linphone
211M	./Code drop 1-6
576K	./.Skype
900K	./workspace
2.7G	./secure
33G	.
33G	total
anil@anil-HP-EliteBook-8440p:~$ 

---

### Post by anilp on 2011-01-19
It seems that the problem is with /tmp

> cp: writing `/tmp/tmpX2KZDc/system.image': No space left on device

However, when I right-click on properties, I see it has 51 items, totalling 130.5 KB

anil@anil-HP-EliteBook-8440p:/tmp$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev

Any help appreciated.

---

