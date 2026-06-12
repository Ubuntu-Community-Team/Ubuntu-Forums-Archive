---
title: "auto start raid array"
date: 2010-12-04
forum: General Help
---

### Post by MonsterMaxx on 2010-12-04
I've created a soft raid w/ 2x 1TB drives by using Disk Utility.
(used for mythtv storage, not system, swap or anything else)

If I start the raid array in the Disk Utility mount and everything works as it should, but on reboot the raid array isn't started so I have to go into Disk Utility, start it, then run the mount.

How can I get it to start automatically?

Thanks in advance.

---

### Post by ronparent on 2010-12-05
Add the partition you want to auto mount to /etc/fstab. I think you have to sudo gedit it to save the changes. You can mimic the syntax used for other fstab entries. Good luck.

---

### Post by MonsterMaxx on 2010-12-05
That's what I had.

What it needs is to auto start the array, not auto mount.

To start the array I have to go into disk utility, select the array and press 'start array'.  From there I can mount -a to rescan fstab.

---

### Post by MonsterMaxx on 2010-12-06
bump

---

### Post by piratebill on 2010-12-06
if you have mdadm installed run this:

 ```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```


or just run sudo mdadm --detail --scan and append the output to mdadm's conf file


note: this works great if the disk utility created the Raid using mdadm.  If it didn't, this may not do anything.  If that is the case I would recreate your raid using mdadm

---

### Post by MonsterMaxx on 2010-12-06
Thanks, but it didn't work.  On reboot the array is not 'started'.  I have to go into disk utility and start the array.  Then from a root command prompt mount -a and it's all running.

I'm pretty sure it's used mdadm because when I first did it it wouldn't complete saying mdadm wasn't in the machine.  Did an apt-get to install mdadm and then disk utility worked to create the raid.

It's working, but a pita on every reboot.

Here's the results of mdadm scan
```
ARRAY /dev/md0 level=raid0 num-devices=2 metadata=01.02 name=:New RAID Array UUID=9c0943d6:42444a2b:a8fe5f93:fc0cc750
```

---

### Post by piratebill on 2010-12-06
what is the output of your mdadm.conf and your fstab?

---

### Post by MonsterMaxx on 2010-12-06
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
# ARRAY /dev/md/New RAID Array level=raid0 metadata=1.2 num-devices=2 UUID=674f521d:07a67cb4:9a2607d8:e69c4e93 name=:New RAID Array

# This file was auto-generated on Sun, 05 Dec 2010 13:34:48 -0500
# by mkconf $Id$

# added by mdadm --detail --scan >> /etc/mdadm/mdadm.conf
ARRAY /dev/md0 level=raid0 num-devices=2 metadata=01.02 name=:New RAID Array UUID=9c0943d6:42444a2b:a8fe5f93:fc0cc750
```

note: it was tossing errors about that first ARRAY line so I commented it out figuring the new one replaced it anyway

---

### Post by piratebill on 2010-12-06
So far your mdadm.conf looks good (good idea to comment out the old line).  Don't know about your fstab though.

run this:
```
 sudo blkid /dev/md0p1
```

then add it to your fstab.  My server's fstab looks like this:

```
UUID=ab8d28d7-8112-4206-bd87-ca488f70cfb8 /Raid ext4    errors=remount-ro 0       1

```

just replace the UUID with what ever blkid spat out, change the mount point and whatever filesystem your using.  Everything should work then.

---

### Post by MonsterMaxx on 2010-12-07
ok, tried that. same results.
here's my fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=0e873243-9139-4e28-8ad8-c20286abdee2 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=a8c488a9-13c7-4d57-ac1a-4a4d55136f8a /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=e1c6b139-7b73-4896-bfa9-faff8a16c151 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=dbdb49eb-a073-4f60-8e7b-2b793fb5662e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Raid was /dev/md0
UUID=7a62eb97-55e0-4b04-8ff3-6cf0e09b1fc6 /storage           ext4    defaults        0       0
```

Maybe I'm not explaining this right.  I've tried a couple screen shots of what I have to do in disk utility to make the raid start.  Hopefully that will help.

---

### Post by piratebill on 2010-12-07
I'm at a loss.  The line in the mdadm.conf should be starting your array.  Maybe mdadm isn't starting as a daemon when your computer boots?  I think I see an issue in your fstab, but that shouldn't have any effect on mdadm not starting the array.  This is a long shot (and I'm probably wrong) but in your fstab you are trying to automount md0, not md0**p1**.  Maybe its erroring out and causing the raid to stop?  when you first turn on your computer what is the output of 

```
cat /proc/mdstat
```

---

### Post by parsim on 2010-12-07
Is mdadm starting on boot? I.e. before you manually start the array, do you get output like this:
```
$ ps ax | grep mdadm
 1647 ?        Ss     0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
 3119 pts/0    S+     0:00 grep mdadm
```
If not, you might want to try:
```
update-rc.d mdadm defaults
```
... and make sure things look like this:
```
$ ls -l /etc/rc?.d/*mdadm*
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc0.d/K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc1.d/K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc2.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc3.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc4.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc5.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-01 14:52 /etc/rc6.d/K25mdadm -> ../init.d/mdadm
```
I'm no expert on this, just some ideas.

---

### Post by MonsterMaxx on 2010-12-07
After boot.  During boot it says something like 
cannot find /storage press S to skip  (I press s and it does.)
```
robin@MythTV-SRV:~$ sudo -i
[sudo] password for robin: 
root@MythTV-SRV:~# ^C
root@MythTV-SRV:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
root@MythTV-SRV:~#  ps ax | grep mdadm
 1572 ?        Ss     0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
 2326 pts/0    S+     0:00 grep --color=auto mdadm
root@MythTV-SRV:~# ls -l /etc/rc?.d/*mdadm*
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc0.d/K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc1.d/K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc2.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc3.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc4.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc5.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc6.d/K25mdadm -> ../init.d/mdadm
root@MythTV-SRV:~# 

```

now I've gone in and started the the raid like in the two screen shots
```

root@MythTV-SRV:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdd1[0] sdc1[1]
      1953519616 blocks super 1.2 512k chunks
      
unused devices: <none>
root@MythTV-SRV:~# ls -l /etc/rc?.d/*mdadm*
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc0.d/K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc1.d/K25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc2.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc3.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc4.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc5.d/S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root 15 2010-12-05 13:34 /etc/rc6.d/K25mdadm -> ../init.d/mdadm
root@MythTV-SRV:~#
```

---

### Post by piratebill on 2010-12-07
It looks like the daemon is running.  The cannot fine /storage is an fstab issue (fstab cannot mount the raid because it has not started). The only thing I can suggest (as painful as it might be) is to rebuild the array using mdadm.  Hopefully someone more knowledgeable than I will have a better solution.

This is what I did to create my array (that auto starts just fine):
formatted the disks with fdisk and changed the partition type to Linux raid autodetect
(guessing on actual fdisk commands...dont have a nix box right here) 
```
fdisk /dev/sdb (use whatever drives you have)
```
format the disk, then use the -t option to change the type to Linux raid autodetect

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

watch the array using
```
watch cat /proc/mdstat
```

then after that run
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

after it is built format the raid
```
fdisk /dev/md0p1
```

after all that the array should work and auto start fine.


Wish I had an exact solution for you :-k

---

### Post by parsim on 2010-12-08
> **MonsterMaxx said:**
> After boot.  During boot it says something like 
cannot find /storage press S to skip  (I press s and it does.)

Well this is clearly the problem, so you should pay more attention to what it says. Start with a precise error message.

---

### Post by u-slayer on 2010-12-08
I have the opposite problem. No matter what I do I can't get mdadm to **not auto start** the array. 

I have a startup script that always gets run, and I want it to do some checks before starting.

Here's my mdadm.conf I commented out the raid array, but it still manages to start everything no matter what I do.

```

#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid5 num-devices=4 UUID=3598a12f:6121:4de5:978c:ba07c6d6c88d

# This file was auto-generated on Tue, 25 May 2010 21:49:30 -0500


```

---

### Post by MonsterMaxx on 2010-12-14
bump

---

### Post by rubylaser on 2010-12-14
u-slayer not really related to the original post, but you could just run
```
dpkg-reconfigure mdadm
```

And tell it not to auto start arrays.

---

### Post by rubylaser on 2010-12-14
MonsterMaxx,

If mdadm is starting, but not initialized prior to the filesystems, you could write an init script to mount the array after boot like this.

Comment out / remove this line from /etc/fstab
```
UUID=7a62eb97-55e0-4b04-8ff3-6cf0e09b1fc6 /storage           ext4    defaults        0       0

```

Then do this...

```
sudo nano /etc/init.d/mount_raid
```
paste in&#8230;
```
#! /bin/bash
mount -t ext4 /dev/md0 /storage
```
```
chmod 755 /etc/init.d/mount_raid
```
```
update-rc.d mount_raid defaults
```

This is kind of a hack, but should automount your array after boot. I hope that helps.

---

### Post by MonsterMaxx on 2010-12-14
{code]update-rc.d mount_raid defaults
update-rc.d: warning: /etc/init.d/mount_raid missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/mount_raid ...
   /etc/rc0.d/K20mount_raid -> ../init.d/mount_raid
   /etc/rc1.d/K20mount_raid -> ../init.d/mount_raid
   /etc/rc6.d/K20mount_raid -> ../init.d/mount_raid
   /etc/rc2.d/S20mount_raid -> ../init.d/mount_raid
   /etc/rc3.d/S20mount_raid -> ../init.d/mount_raid
   /etc/rc4.d/S20mount_raid -> ../init.d/mount_raid
   /etc/rc5.d/S20mount_raid -> ../init.d/mount_raid[/code]

---

### Post by u-slayer on 2010-12-14
> **rubylaser said:**
> u-slayer not really related to the original post, but you could just run
```
dpkg-reconfigure mdadm
```

And tell it not to auto start arrays.


I ran that command and I only get these questions:
```
Should mdadm run monthly redundancy checks of the MD arrays? 
Do you want to start the MD monitoring daemon?
Do you want to boot your system if your RAID becomes degraded? 
```

None of those stop mdadm from assembling my arrays.

---

### Post by SaturnusDJ on 2010-12-15
I think the command
```
update-initramfs -u
```
is needed after generating a config in /etc/mdadm/mdadm.conf and /etc/fstab.

This should do some stuff to the bootimage so the array will start at boot.


Not sure however (because this makes not much sense when the array does not contain the OS), but if this works for MonsterMaxx, it might also work for u-slayer to use this command.

---

### Post by MonsterMaxx on 2010-12-16
```
root@MythTV-SRV:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
mdadm: metadata format 01.02 unknown, ignored.
mdadm: unrecognised word on ARRAY line: RAID
mdadm: unrecognised word on ARRAY line: Array
root@MythTV-SRV:~# 
```

---

### Post by piratebill on 2010-12-16
Doing some reading I found this.  Might help
[http://ubuntuforums.org/showthread.php?t=1468064](http://ubuntuforums.org/showthread.php?t=1468064)

---

