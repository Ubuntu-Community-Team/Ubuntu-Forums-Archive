---
title: "Ubuntu install WHOOPS! Now running out of space on / partition What to do? Screenshot"
date: 2012-08-30
forum: General Help
---

### Post by 777funk on 2012-08-30
I followed[ this guy's steps ]("http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/")when I installed my dual boot and it seems like I'm running out of space (at 86% in the picture). Check out this screenshot to see what I mean. 

I notice that my / Directory is getting less and less available space as I install programs. So what did I do wrong? or more important, what should I do now?

thanks,
Nick

---

### Post by dragonfly41 on 2012-08-30
install and use bleachbit to clean up

---

### Post by oldfred on 2012-08-30
I have not used bleachbit but that is often suggested.

He says recommended is 4.4 but that is the absolute minimum size that Ubuntu will install into. But updates & adding software use more space. I normally suggest 10 to 25GB for / (root) and no separate /boot for most systems.  And only the smaller / sizes for those with smaller drives. I install to 25GB and use between 7 and 9GB with all data in other partitions. 

Is your /home mounted? 

Post this:

```
mount
```

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by 777funk on 2012-08-30
> **oldfred said:**
> 

Is your /home mounted? 

Post this:

```
mount
```HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)


```
nick@NickUbuntu:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdf1 on /mnt/Windows type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /boot type ext4 (rw)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nick)
```

---

### Post by AMSlider on 2012-08-30
I'd boot a live CD and run gparted to shrink sda6 to reclaim some space, then increase sda5 to at least 25GB or whatever you think you might need.

HTH

---

### Post by 777funk on 2012-08-30
I'm thinking of trying another distro of Ubuntu (just to see). So I may just start over! This time I'll probably just pop the CD in and let it do it's thing.

OTOH, what if I decided to do it manually again. Is there a good/smarter way to keep things laid out?

---

### Post by oldfred on 2012-08-30
If you let it do it automatically it just creates / (root) and swap. 

What were you installing that took so much room, but again I suggest 25GB for / and a separate /home. You usually do not need a separate /boot, but some very old systems and for whatever reason, some new system need a /boot if drive is very large and / becomes over 100GB. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by pqwoerituytrueiwoq on 2012-08-31
[FONT=Courier New]sudo apt-get autoclean[/FONT]
i usually give root 16gb
i am using 6.7gb for root on my 3.5 year install of 10.04
i have a separate /var, /tmp and /home

---

### Post by mastablasta on 2012-08-31
you can use Ubuntu tweak programme to clean old kernels off your mashcine. that should help you reclaim plenty space back. i have 8GB for the OS and home. it seems to be enough as long as i delete the kernels every no wand then. leaves me with about 2-2.5GB. using Xubuntu....

---

### Post by 777funk on 2012-09-10
> **AMSlider said:**
> I'd boot a live CD and run gparted to shrink sda6 to reclaim some space, then increase sda5 to at least 25GB or whatever you think you might need.

HTH


Would it be possible to just delete one partition and open up the space?

---

### Post by 777funk on 2012-09-14
> **AMSlider said:**
> I'd boot a live CD and run gparted to shrink sda6 to reclaim some space, then increase sda5 to at least 25GB or whatever you think you might need.

HTH

I used this method... worked pretty good. I had disk errors at first (red exclamation point above the partition I shrunk) but I ran error fix and it worked perfectly. A few keyboard shortcut settings were lost (not positive this was related), but so far that's the only thing I've noticed wrong with my install at this point.

---

