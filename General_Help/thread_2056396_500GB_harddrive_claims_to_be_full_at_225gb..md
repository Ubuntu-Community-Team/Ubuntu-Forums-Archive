---
title: "500GB harddrive claims to be full at 225gb."
date: 2012-09-11
forum: General Help
---

### Post by bobman321123 on 2012-09-11
Yeah, I really can't give much more detail than the title. 
Any idea why this is happening?

---

### Post by SlugSlug on 2012-09-11
please post output of

```
df -h
```

```
fdisk -l
```

---

### Post by Wim Sturkenboom on 2012-09-11
> 
Yeah, I really can't give much more detail than the title. 

Of course you can :)

Which command / application is stating this? df? dh? Some graphical nonsense?

Also, in addition to the earlier commands in post #2, please post the output of the mount command
```

mount

```

---

### Post by bobman321123 on 2012-09-11
df - h
```
/dev/sda5        25G   24G  285M  99% /
udev            3.9G   12K  3.9G   1% /dev
tmpfs           1.6G  948K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  2.3M  3.9G   1% /run/shm
/dev/sda2       294G   63G  232G  22% /mnt/data
/dev/sda7        50G   49G  996M  99% /media/3A9E3E5E31D6AD88
/dev/sda1        90G   75G   16G  83% /media/2A0839BF08398B39

```

fdisk -l had no output

 mount
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /mnt/data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda7 on /media/3A9E3E5E31D6AD88 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/2A0839BF08398B39 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/joshua/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joshua)
```

---

### Post by SlugSlug on 2012-09-11
your / is full not your drive

either clear out some stuff or mount /home on a diff partition 

/ has 25 gig thats enough if you keep your personal data else where

there are many guides on here to move /home but to confirm please post output of 

```
sudo du -sch /home
```

---

### Post by bobman321123 on 2012-09-11
That's just the thing, I have nothing in my /home but softlinks to my storage partition.

---

### Post by SlugSlug on 2012-09-11
ok post 

```
sudo du -sch /
```

---

### Post by oldfred on 2012-09-11
You may want to do some housecleaning.

I have links to my /mnt/data but still have .wine in /home and Picasa keeps growing. Log files & histories always keep growing, but should not be huge unless you have an error an some log file is going berserk.  
Otherwise the only times my / has grown is when I forgot to mount my backup partition and it defaulted to in /. 

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

Some more command line ways to show use:
#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
find . -maxdepth 1 -type d ! -name . -exec du -sh '{}' \; | sort -h
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by bobman321123 on 2012-09-11
> **SlugSlug said:**
> ok post 

```
sudo du -sch /
```
```

du: cannot access `/home/joshua/.gvfs': Permission denied
11G    /home
11G    total

```

---

### Post by SlugSlug on 2012-09-11
yer you need to shift some of that data or move your /home

---

### Post by oldfred on 2012-09-11
I ran the same command and it tells me I have 80GB. But my / (root) including /home is only 28GB. But I think it follows links and finds  my data partitions and includes that in the count.

sudo du -sch /
{some files it cannot mount as active)
80G    total

fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  8.9G   18G  34% /

This lists every folder

fred@fred-Precise:~$ sudo du -hc --max-depth=1
108K    ./.compiz-1
1.3G    ./.wine
40K    ./Desktop
etc - many folders
1.7G    total

So my /home is 1.7GB and .wine is 1.3GB of that. I have moved some of the hidden folders that are large like Firefox & Thunderbird profiles to data partitions.

---

### Post by jerome1232 on 2012-09-11
I believe you need to add the -x option to prevent it from traversing file-systems. Mine also refuses to follow symlinks unless I add the -L flag to dereference symlinks.

```
sudo du -hx --max-depth=1 / 2> /dev/null
```

---

### Post by Wim Sturkenboom on 2012-09-12
I suggest that you run your 'tests' in single user mode (recovery mode) as root user. Unmount everything that you don't need (/media/... and /mnt/data). Your problem might be caused by a failed mount (or you unmounted a partition and forgot) in the past and data got written in the directory instead of in the mounted partition.

---

### Post by bobman321123 on 2012-09-15
```
du: cannot access `./.gvfs': Permission denied
981M    .
981M    total

```

I ran the command today, and this is what it gave me. 
"System Monitor" is still telling me that I have  1.5GB left on a 25GB partition. 
Is this just because of applications then?

---

### Post by SeijiSensei on 2012-09-15
> **bobman321123 said:**
> df - h
```
/dev/sda5        25G   24G  285M  99% /
udev            3.9G   12K  3.9G   1% /dev
tmpfs           1.6G  948K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  2.3M  3.9G   1% /run/shm
/dev/sda2       294G   63G  232G  22% /mnt/data
/dev/sda7        50G   49G  996M  99% /media/3A9E3E5E31D6AD88
/dev/sda1        90G   75G   16G  83% /media/2A0839BF08398B39

```

Your drive (called /dev/sda) is divided into a bunch of different partitions.  Run the command "sudo fdisk -l /dev/sda" to see the complete list.  You have a lot of empty space in /mnt/data.  Try moving stuff from your home directory to that.  You'll need to have write permissions in /mnt/data of course.

Even better, create a "symbolic link" to /mnt/data from your home directory like this:
```

cd ~
ln -s /mnt/data

```

Now you will see the contents of /mnt/data appear as "data" in your home directory.  You can read and write to it as if it were in the home directory itself.  Move some stuff out of your home directory into /mnt/data to free up space on the root filesystem "/".

Did you organize the disk yourself?  /mnt/data is not a location that Ubuntu will create by default.

---

### Post by Wim Sturkenboom on 2012-09-16
> **bobman321123 said:**
> fdisk -l had no output
That needs to be run as root, so add 'sudo' to it (as SeijiSensei states) if you're not in recovery mode already.

> **bobman321123 said:**
> ```
du: cannot access `./.gvfs': Permission denied
981M    .
981M    total

```

I ran the command today, and this is what it gave me. 
"System Monitor" is still telling me that I have  1.5GB left on a 25GB partition. 
Is this just because of applications then?
Which command? I think that you don't run the complete command(s) as given by us because your output does not make sense; you probably forgot the '/' in the command posted in post #12, so you're running it on your home directory instead of on the whole system.

For example, my output
```

wim@i3-2120:~$ **[COLOR="Blue"]sudo du -h --max-depth=1 / 2> /dev/null[/COLOR]**
[sudo] password for wim: 
14M	/etc
4,0K	/lib64
4,0K	/media
16K	/lost+found
47M	/boot
4,0K	/selinux
0	/sys
36K	/mnt
27G	/home
48K	/tmp
2,4G	/usr
104K	/root
8,8M	/bin
0	/proc
4,0K	/opt
4,0K	/dev
4,0K	/cdrom
4,0K	/srv
1,1M	/run
356M	/lib
468M	/var
8,7M	/sbin
30G	/
wim@i3-2120:~$ 

```
Again, in recovery mode and dropped to a root shell, you don't need sudo. 

And no, it's not necessarily programs that you have installed that occupy the space. A lot of space can be occupied by log files in /var/log.

PS
unmount your /mnt/data; if anything is underneath it, you will not see it with du if it's mounted.

---

