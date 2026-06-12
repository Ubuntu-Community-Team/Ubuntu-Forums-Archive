---
title: "320gb hard drive filled up with an Ubuntu installation?"
date: 2010-02-28
forum: General Help
---

### Post by Nugar on 2010-02-28
Hi all,

A month or so ago, I built a new box. I installed a previously used 320gb hard drive and a newly bought 1TB hard drive.

Before formatting anything, I copied all the contents from the 320gb hd to the 1tb hd using windows, since at that time for some reason I couldn't get Ubuntu to read the 1tb drive.

At some point, I managed to format the 1tb drive as ext3 (don't know why I didn't have the ext4 option), and copied the files I wanted backed up from the 320gb to the 1tb drive.

Once I did that, I prepared to delete the files from the 320gb drive. The thing is I can't find them anymore. I had made a /Storage directory, and now the 1tb is called like that too.

The thing is, the 320gb drive is almost full, but it only has my Ubuntu installation. I keep my file in the 1tb drive, so the 320 should be fairly empty. How large can a Ubuntu installation get? 300+ GB???

Where should I look to see what I'm using the space with? I think (this was about two months ago) I created a directory Storagetempo or something like that. How would I look for it?

I realize a solution could  be just reinstalling Ubuntu on the 320gb drive, since I have all my other files on the 1tb, but that seems too "windowy" to me.

Any pointers about how to proceed here?

Thanks in advance,

---

### Post by Richard1979 on 2010-02-28
The Ubuntu installation should only be about 3GB tops.

Try running "du -h /home | less" in a console.
This might help you see where the space is being used.

---

### Post by Nugar on 2010-02-28
Thanks Richard,

But the home directory itself isn't even 1gb. Is it possible to do this kind of search, but specifying say, a size threshold? Like show me all directories larger than ***?

Thanks,

---

### Post by SecretCode on 2010-02-28
Try command-line:
```
du -hx --max-depth 1 /
```
and if /var is the biggest, then 
```
du -hx --max-depth 1 /var
```
At each step you can see which directory is taking the most space, and zoom in on it.

Or GUI: baobab (applications > accessories > disk usage analyser)

---

### Post by Nugar on 2010-02-28
Thanks! I'll do that

Cheers,

---

### Post by gfuggs on 2010-02-28
What output do you get from "sudo fdisk -l", "mount", and "df"?

---

### Post by Nugar on 2010-02-28
Here's the output:

fdisk -l
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9566c6a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      120168   965249428+  83  Linux
/dev/sda2          120169      121601    11510572+   f  W95 Ext'd (LBA)
/dev/sda5          120169      121601    11510541   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18ba18b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37433   300680541   83  Linux
/dev/sdb2           37434       38913    11888100    5  Extended
/dev/sdb5           37434       38913    11888068+  82  Linux swap / Solaris

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b627b1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20023   160834716    b  W95 FAT32


```
mount:

```

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /media/Storage type ext3 (rw,errors=remount-ro)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/IOMEGA_HDD type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
gvfs-fuse-daemon on /home/nugar/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nugar)

```df:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            295952312 192609720  88308568  69% /
udev                   2029172       276   2028896   1% /dev
none                   2029172      1724   2027448   1% /dev/shm
none                   2029172       376   2028796   1% /var/run
none                   2029172         0   2029172   0% /var/lock
none                   2029172         0   2029172   0% /lib/init/rw
/dev/sda1            950102504 402743260 499096776  45% /media/Storage
/dev/sdc1            160795424  26568480 134226944  17% /media/IOMEGA_HDD


```

---

### Post by gfuggs on 2010-02-28
I was thinking that maybe there was a partition not being mounted, but it doesn't look like that's the case.

It does look like there is a directory somewhere that you've lost track of.  To find it, try "sudo du -sh /*"
That will give you the overall size of each directory in /.
Once you find the directory that's a few hundred GB in size, for example /home, then you can do "sudo du -sh /home/*", and keep narrowing it down like that.

Off the top of my head, I'm not sure if it will count the other mounted drives in /media, but if it does you can obviously ignore them.

---

### Post by Nugar on 2010-02-28
I'll do that. It does seem to count the drives mounted in media, but I'll analize what it says about the others...

Thanks!

---

### Post by Nugar on 2010-03-01
Yesterday I went away from keyboard since my daughter was dancing in tv :)

Ok, I did a sudo du -sh /* and among other things I get this:

```

16K    /lost+found
410G    /media
4.0K    /mnt
491M    /opt
{snip}
0    /proc
175G    /root
9.2M    /sbin
4.0K    /selinux
```As you can see the /media directory is in fact counted.

But what seems interesting is the 175G /root directory. Is this normal? Also, I tried sudo du -sh /root/* and I got:

```
du: cannot access `/root/*': No such file or directory

```How can I see what's inside that directory? I get permission denied even doing a sudo.

Thanks in advance,

---

### Post by SecretCode on 2010-03-01
Please add the -x parameter so as to be sure files on external drives are not counted.
```
sudo du -shx /*
```

For /root, because you don't have read access, the shell expansion of * breaks. (At least I think this is what's happening.) Try the --max-depth parameter instead of -s.
```
sudo du -hx --max-depth 1 /root
```

It's unusual to have such a lot of data in /root - something was probably accidentally copied there.

---

### Post by Nugar on 2010-03-01
Also, I enabled the root account on this machine and upon entering the /root directory, the only thing that appears there is a Desktop directory, which appears as empty:

```

root@nugar-desktop:/# du -sh /root/*
4.0K    /root/Desktop
root@nugar-desktop:/# cd root
root@nugar-desktop:~# ls
Desktop
root@nugar-desktop:~# du -sh /root/Desktop
4.0K    /root/Desktop
root@nugar-desktop:~# du -sh Desktop/*
du: cannot access `Desktop/*': No such file or directory
root@nugar-desktop:~# du -sh ./Desktop/*
du: cannot access `./Desktop/*': No such file or directory
root@nugar-desktop:~# 

```Any clues as to how to find out what those 175gb are?

(I disabled the root account again)

Cheers,

---

### Post by plucky on 2010-03-01
From a terminal ```
sudo find / -name '*' -size +500M
``` will search for files greater than 500M.If nothing found just reduce the value and try again.

Good Luck

---

### Post by MJBoa on 2010-03-01
Well, I would say just try 

```
ls -al /root
```

The -al switch lists even hidden files in a list format.

---

### Post by SecretCode on 2010-03-01
> **Nugar said:**
> Also, I enabled the root account on this machine and upon entering the /root directory, the only thing that appears there is a Desktop directory, which appears as empty:

...

Have you tried my suggestions yet or should I ignore this thread?

> **SecretCode said:**
> Try command-line:
```
du -hx --max-depth 1 /
```
and if /var is the biggest, then 
```
du -hx --max-depth 1 /var
```
At each step you can see which directory is taking the most space, and zoom in on it.

Or GUI: baobab (applications > accessories > disk usage analyser)

> **SecretCode said:**
> Please add the -x parameter so as to be sure files on external drives are not counted.
```
sudo du -shx /*
```

For /root, because you don't have read access, the shell expansion of * breaks. (At least I think this is what's happening.) Try the --max-depth parameter instead of -s.
```
sudo du -hx --max-depth 1 /root
```

It's unusual to have such a lot of data in /root - something was probably accidentally copied there.

---

### Post by Nugar on 2010-03-01
Hi all,

Right now I'm at work on a XP box, so I haven't been able to try your suggestions. Once I get home around 5pm (I'm at -5gmt) I'll try them and see and come back to you.

Thanks for all the pointers here! Somehow I'm sure the answer will be in that /root directory, something huge there that I can't read.

Cheers,

---

### Post by SecretCode on 2010-03-01
Remember it might be one or more files in /root itself, not necessarily subdirectories.

---

### Post by Nugar on 2010-03-01
I'll keep that in mind :)

---

### Post by Nugar on 2010-03-01
Hi again all,

I've done some things. Let's see. Just for the sake of finding what is going on, I enabled root in Ubuntu.

I did a ls -la and got this:

```
root@nugar-desktop:~# ls -la
total 116
drwx------ 22 root root 4096 2010-02-25 06:46 .
drwxr-xr-x 23 root root 4096 2010-02-10 21:53 ..
drwx------  2 root root 4096 2010-01-25 19:24 .aptitude
-rw-------  1 root root  252 2010-03-01 07:28 .bash_history
-rw-r--r--  1 root root 2227 2009-04-27 04:56 .bashrc
drwxr-xr-x  3 root root 4096 2010-01-18 16:43 .cache
drwx------  3 root root 4096 2010-01-18 18:08 .config
drwx------  3 root root 4096 2010-01-17 12:43 .dbus
drwxr-xr-x  2 root root 4096 2010-01-25 19:29 .debtags
drwxr-xr-x  2 root root 4096 2010-01-17 12:43 Desktop
drwxr-xr-x  3 root root 4096 2010-01-17 18:36 .emerald
-rw-------  1 root root   16 2010-01-17 15:55 .esd_auth
drwx------  3 root root 4096 2010-02-27 21:40 .gconf
drwx------  2 root root 4096 2010-02-27 21:40 .gconfd
drwxr-xr-x  6 root root 4096 2010-01-18 16:43 .gnome2
drwx------  2 root root 4096 2010-01-17 14:41 .gnome2_private
drwxr-xr-x  2 root root 4096 2010-02-12 21:08 .gstreamer-0.10
drwx------  3 root root 4096 2010-01-17 20:15 .kde
drwx------  3 root root 4096 2010-01-17 16:20 .local
drwxr-xr-x  2 root root 4096 2010-01-17 12:43 .nautilus
-rw-r--r--  1 root root 1156 2010-01-17 12:57 .nvidia-settings-rc
-rw-r--r--  1 root root  140 2007-11-19 12:57 .profile
drwx------  2 root root 4096 2010-02-25 06:46 .pulse
-rw-------  1 root root  256 2010-01-17 12:39 .pulse-cookie
-rw-------  1 root root  829 2010-02-25 06:46 .recently-used.xbel
drwx------  3 root root 4096 2010-02-16 07:41 .synaptic
drwx------  4 root root 4096 2010-01-17 17:10 .thumbnails
drwxr-xr-x  2 root root 4096 2010-01-24 23:11 .uml
drwxr-xr-x  2 root root 4096 2009-10-27 13:15 .wapi

```As you can see there are several directories there.

So then I did du -hx --max-depth 1 and got this:

```
4.0K    ./Desktop
12K    ./.dbus
12K    ./.cache
4.0K    ./.uml
104K    ./.emerald
4.0K    ./.gnome2_private
4.0K    ./.nautilus
12K    ./.config
88K    ./.gconf
8.0K    ./.gconfd
4.0K    ./.wapi
136K    ./.synaptic
572K    ./.gstreamer-0.10
4.0K    ./.debtags
460K    ./.thumbnails
175G    ./.local
12K    ./.kde
52K    ./.gnome2
4.0K    ./.aptitude
4.0K    ./.pulse
175G    .

```As you can see, it seems that the large directory is ./.local

I kept going and found that ./Trash had the 175gb files. And kept going deeper and there it was!

I found the set of directories I had backed up when installing the machine at first and that I'd in fact "watch" disappear.

So I just deleted that and I have my space back :)

Many thanks to all that helped, SecretCode, MJBoa, plucky, Richard1979, gfuggs, 

I'm now off to deactivate the root user ;)

Cheers,

---

