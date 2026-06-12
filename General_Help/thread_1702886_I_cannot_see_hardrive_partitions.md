---
title: "I cannot see hardrive partitions ?"
date: 2011-03-08
forum: General Help
---

### Post by BADGER.BRAD on 2011-03-08
Hello all,

I have recently reinstalled Ubuntu. As the last operating system developed a problem (Xubuntu) and I lost all my files I decided this time to partition the drive so that anything important could be backed up to the other partition.The problem I have now is I cannot work out how to see the other 40Gb of the drive in order to copy the files over. Ubuntu shows 120ish gig for its portion which is as I set it up.

Any help appreciated.

Brad

---

### Post by jerome1232 on 2011-03-08
They should be listed under the places menu.

What is the output of the follow two commands?

```
mount
sudo fdisk -l
```

---

### Post by BADGER.BRAD on 2011-03-08
Mount = dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/badger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=badger

sudo fdisk -l = Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d03cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17438   140062720   83  Linux
/dev/sda2           17438       17734     2382849    5  Extended
/dev/sda5           17438       17734     2382848   82  Linux swap / Solaris

Many thanks

Brad

---

### Post by jerome1232 on 2011-03-08
According to that you only have one partition, your root partition, which is 130 GB's. You also have a 2.3 GB swap partition which get's used by the system in the same was as a swap file get's used by windows.

So I assume you didn't create the backup partition and just left part of the drive unallocated?

If that's the case you need to install gparted and create a partition.

---

### Post by BADGER.BRAD on 2011-03-08
Sounds very much as I did ! Never gave it a name.

Many thanks.

Brad

---

### Post by BADGER.BRAD on 2011-03-08
Hello Again Jerome,

I now have partition showing (using Gparted) but get this message when I try and copy data to it, any ideas.

The folder "xyz" cannot be copied because you do not have permissions to create it in the destination.

Many thanks

Brad

---

### Post by jerome1232 on 2011-03-08
Sounds like you need to set permissions up. 

So make sure your user has write access. Replace the text in bold with the real mount point. If you aren't sure of the mount point you can check with the "mount" command.

```
sudo chown $USER:$USER **/mnt/mountpoint**
sudo chmod u+w **/mnt/mountpoint**


#To check mount points
mount
```


It's best to add an fstab entry (fstab is a file that lists partitions to be automatically mounted during boot time, it also set's up mount options for them)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Hope this helps.

---

### Post by BADGER.BRAD on 2011-03-08
Hello Again Jerome,

I'm getting near to kicking the computer in the air at the moment or worse than that installing windows XP for the first time in 5 years, I've had 2 crashes and loss of all my data in the passed week.This is what I get after following your instructions.
badger@badger-desktop:~$ sudo chown badger:badger /mnt//dev/sda3
chown: cannot access `/mnt//dev/sda3': No such file or directory
badger@badger-desktop:~$ sudo chmod u+w /mnt//dev/s

Any more ideas.

Again many thanks for all your help.

Brad

---

### Post by jerome1232 on 2011-03-08
Post the output of mount, copy and paste the output and put code tags around it like this, I'm about to goto sleep so it might be a bit before I can reply
[noparse]```
my output here
```[/noparse]

```
mount
```


edit: I can certainly understand getting frustrated with it! Believe me I blew up my server's hard disk drive a couple weeks ago and am still getting that thing setup the way I had it.

---

### Post by BADGER.BRAD on 2011-03-09
[CODE]badger@badger-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/badger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=badger)
/dev/sda3 on /media/BACKUP type ext2 (rw,nosuid,nodev,uhelper=udisks)
badger@badger-desktop:~$ [CODE]

I  think I've done as you asked ( hopefully so ! )

Sorry for the delay but I've had a long day today 15 hours at work, Thanks again for all your help Jerome.

Brad

---

### Post by jerome1232 on 2011-03-09
> **BADGER.BRAD said:**
> 
/dev/sda3 on [COLOR="Red"]/media/BACKUP[/COLOR] type ext2 


Ok Highlighted in red is the mount point to your partition.

So to change it's permissions we'd do this

```
sudo chown $USER:$USER /media/BACKUP
```

---

### Post by BADGER.BRAD on 2011-03-10
Wow it is possible after all just as I was giving up all hope, it now works ! Thanks for your patience Jerome it really is much appreciated. May the force be with you.

Brad

---

