---
title: "Can't free up unused disk space"
date: 2010-10-08
forum: General Help
---

### Post by Wafaa on 2010-10-08
I seem to have a strange problem with disk usage on my linux partition. I just upgraded my 10.04 to 10.10 and I'm not sure if this was there before.

My nautilus tells me that I have 1.4 GB free on my linux partition. My partition editor (GParted) tells me that 79.31 GB of my 81.38 GB is used, and I've 2.08 GB free. There's no way I've got that much stuff on my linux partition, and to confirm it, I ran the Disk Usage Analyzer (from Applications/Accessories), and the total size of everything on that partition amounts to much less than 10 GB.

I've tried deleting all my trash (both root and user trash) and I looked at all the folders trying to find any suspiciously large ones to no avail. I thought it might be some weird bug, but removing some files, added the correct amount of space to the free space detected by nautilus. I have no idea what eating up my disk space.

Help Please!! :confused:

---

### Post by slooksterpsv on 2010-10-08
I've had this problem before, and it was the .xsession_errors.old file in your home folder. If you open nautilus in your home folder, press CTRL+H to show hidden files, see how big .xsession_errors.old is.

---

### Post by jbrown96 on 2010-10-08
Post the output of the following 

```
mount -l
df -h
find / -maxdepth 1 -exec du -hs {} \;
```

---

### Post by Wafaa on 2010-10-08
> ~$ mount -l
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda5 on /media/Drive D type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/WINDOWS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wafaa/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wafaa)

~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              13G   11G  1.5G  88% /
none                  1.5G  296K  1.5G   1% /dev
none                  1.5G   88K  1.5G   1% /dev/shm
none                  1.5G  212K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda5             196G  162G   34G  83% /media/Drive D
/dev/sda1              20G   17G  3.6G  83% /media/WINDOWS

find / -maxdepth 1 -exec du -hs {} \;
du: cannot access `/proc/2048/task/2048/fd/6': No such file or directory
du: cannot access `/proc/2048/task/2048/fdinfo/6': No such file or directory
du: cannot access `/proc/2048/fd/6': No such file or directory
du: cannot access `/proc/2048/fdinfo/6': No such file or directory
du: cannot access `/home/wafaa/.gvfs': Permission denied
188G    /
7.2M    /sbin
1.6G    /var
384K    /dev
7.6M    /lib32
23M    /boot
0    /initrd.img
7.7M    /bin
247M    /opt
4.0K    /selinux
0    /sys
0    /lib64
178G    /media
3.1G    /usr
170M    /lib
4.0K    /cdrom
16K    /lost+found
0    /vmlinuz
du: cannot access `/proc/2073/task/2073/fd/6': No such file or directory
du: cannot access `/proc/2073/task/2073/fdinfo/6': No such file or directory
du: cannot access `/proc/2073/fd/6': No such file or directory
du: cannot access `/proc/2073/fdinfo/6': No such file or directory
0    /proc
52K    /tmp
71M    /root
4.0K    /mnt
17M    /etc
200K    /srv
du: cannot access `/home/xxxx/.gvfs': Permission denied
4.8G    /home
I just noticed that it says that my sda3 is only 13GB, which can't be right, at least not according to GParted. Now I'm worried that the upgrade messed up the partition.

---

### Post by Wafaa on 2010-10-08
@slook 
I don't have an .xsession_errors.old file in my home folder.

---

### Post by jbrown96 on 2010-10-08
There's nothing wrong with your system. All your system files are reasonably sized. Your home directory is 4.8GB, so you could remove some files from there. However, it doesn't make sense to delete stuff just for the sake of disk space.

Keep in mind that 5% of your file systems are reserved fro root. Even though you have 12% free on /, you will get disk errors once that drops to 5%.

You only have 1.5GB free on /. I'm confused why you find that surprising...

---

### Post by slooksterpsv on 2010-10-08
How large does GParted show your / filesystem to be?

---

### Post by Wafaa on 2010-10-08
It's supposed to be 87 GB and that's what GParted and Disk Utility shows, but for some reason it's only showing the 13 GB on Nautilius. 
I think the upgrade messed up the partition or did something. I'll probably just back up my home, do a clean install and see what happens.

---

### Post by slooksterpsv on 2010-10-08
I'd say boot into recovery mode or off of a live cd and run 
fsck -fy

Be sure to backup your data first though.

---

### Post by jbrown96 on 2010-10-08
Your root partition is only 13GB. Your Windows drives, mounted in /media, are substantially larger: 20GB and 196GB.

```
sudo fdisk -l
``` could help determine if your partition are larger than your file system, but that would be an extremely obscure problem that could only occur if you manually set them that way.

---

### Post by Wafaa on 2010-10-08
Thanks for the help guys. I backed up my home and did a clean install, and formatted and reassigned my linux partition. That fixed it. 

While setting my partitions,  I saw that apparently when I upgraded, instead of using the whole 80 GB of the partition, it just left the old 10.04 installation there, made a new 13GB section for 10.10 next to that from the 80GB, and left me unable to access the rest. It seems to do this every time I upgrade instead of doing a clean install. I just now remembered that I had this exact same problem before when I upgraded from 9.10 to 10.04. I don't know if this is a common issue, or for some reason it happens on my laptop. I should just remember to always do a clean install.

---

