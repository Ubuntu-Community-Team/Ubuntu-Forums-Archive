---
title: "Ubuntu boot problem"
date: 2011-05-26
forum: General Help
---

### Post by Xiah on 2011-05-26
When I tried to log in a few days ago i got the below error

After searching around i've got myself a LiveCD to try and fix it because I have files in my /home directory that I can't lose
I've found that it's a memory problem. I've tried "df -ah" in consol and i got the below
```
Filesystem   size      used          avail       use     mounted on
aufs           1.5g        68M          1.5G      5%          /
none           0           0              0           -            /proc
none           0           0              0           -            /sys
fusectl        0            0             0            -           /sys/fs/fuse/connections
none           1.5g         236K       1.5G          1%             /dev
none           0            0             0           -            /dev/pts
/dev/sr0       244m      244M              0            100%         /cdrom
/dev/loop0    204m      204M             0             100%         /rofs
none            0           0             0           -            /sys/kernel/debug
none            0           0             0           -            /sys/kernel/security
none            1.5g       0             1.5G        0%       /dev/shm
tmpfs           1.5g       0             1.5G        0%       /tmp
none            1.5g       60K          1.5G        1%       /var/run
none            1.5g       0              1.5G        0%      /var/lock
```I also tried
ubuntu@ubuntu$  sudo mount /dev/sda1 /mnt ubuntu@ubuntu$ sudo mount -o bind /dev  /mnt/dev ubuntu@ubuntu$ sudo mount -o bind /dev/shm /mnt/dev/shm  ubuntu@ubuntu$ sudo mount -o bind /proc /mnt/proc ubuntu@ubuntu$ sudo  mount -o bind /sys /mnt/sys ubuntu@ubuntu$ sudo chroot /mnt root@ubuntu$  su - fezHowever when I try the "su - fez" I get
-su: cannot create temp file for here-document: no space left on the device

I've  done a few sudo apt-get xxx (can't remember the names) since this  problem on this HDD and they download fine, so there must be space  available.

I've tried plugging the HDD into a second HDD, using  the second one as a master and trying to access /home but there is  nothing in it. I' totally out of idea's, anyone ever heard of this  problem before?

---

### Post by Xiah on 2011-05-26
Bump :(?

---

### Post by Xiah on 2011-05-29
Bump more? :/

---

### Post by linkageless on 2011-05-29
Hello Xiah,
I'm not sure I can solve your problem, but it may be worth including a few additional details. Am I right in assuming that /home is on /dev/sda1 and separate from your root filesystem?

Also what lead you to the conclusion that you have a memory problem? Problems with memory could result in damage to a filesystem, but I would say it's somewhat unusual these days to have a fs completely wrecked.

If you are able can you give us output from:
sudo fdisk -l /dev/sda

and/or your /etc/fstab to aid our understanding.

Last thought - when you mount /dev/sda1 to /mnt are you sure you are mounting from the correct device? Might it be /dev/sdb1 or something?

---

### Post by electrojustin on 2011-05-29
What version of ubuntu are you using?

---

### Post by electrojustin on 2011-05-29
Wait, if /dev/sda1 is in deed the filesystem you boot off of, you should not be mounting it to /mnt. You should mount it to /.

---

### Post by electrojustin on 2011-05-29
Sorry bout the tripple post, but I just thought of a way to test your HDD space. After running fdisk and determining which filesystem contains the directory you boot from, you should mount that filesystem and run df -ah. df -ah only detects mounted filesystems.

---

### Post by linkageless on 2011-05-29
if you believe you have the fs mounted, confirm the details with:
mount

this will hopefully show that it is mounted read-write, maybe a few other relevant details.

---

### Post by oldfred on 2011-05-29
If it really has nothing in it, you may need testdisk or photorec. But did you try running e2fsck on that partition from the liveCD?

From liveCD so everything is unmounted,swap off if necessary, change sda1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by Xiah on 2011-05-29
I'm a little bit of a noob when it comes to this. 
sudo fdisk -l /dev/sda

```
 /dev/sda1   *           1       37767   303355904   83  Linux
/dev/sda2           37767       38914     9212929    5  Extended
/dev/sda5           37767       38914     9212928   82  Linux swap / Solaris 

```When doing mount i get the below 
```
 /dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fez/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fez)
```

I'll give oldfred's idea a test as well and let you know of results, thanks guys :)


*Edit*

Currently using 10.10 on my 2nd HDD and I had 11.04 installed on the HDD that is busted

---

### Post by linkageless on 2011-05-31
An e2fsck on the filesystem from a live cd (while that filesystem is not mounted, read 'man e2fsck') will rule out corruption. I would then mount it up from the live cd and do a 'df -h' to confirm how much space is left.

One interesting fact is that there's a reserved blocks percentage (usually set to 5%) for the use of the root user. This will mean that although 'df -h' may show no space free, root may still be able to write to the device for a while. This and other details about the filesystem can be looked at using 'sudo tune2fs -l /dev/sda1'. Advanced users should see 'man tune2fs' for how to adjust these values. (My preference is to reduce this to say 2% on large / filesystems, and even set to 0 for separate /home/ or other less critical filesystems.)

I'd love to hear how you get on.

---

