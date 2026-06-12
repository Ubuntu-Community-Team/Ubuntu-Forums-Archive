---
title: "Unable to Mount, .ddrescue; Device Busy"
date: 2011-05-18
forum: General Help
---

### Post by Blaze247 on 2011-05-18
A removable internal hard drive was refusing to mount:

 ```
mount -t ext4 /dev/sdc3 /media/backup
```

did nothing. no error no prompt.  When attempting to mount through the disk utility it only caused a loading symbol to get stuck on the partition box.  

The drive is healthy and the data is valuable. I don't know what's going on with the mount so I used ddrescue to back up the partition to an image. I followed the instructions here [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


```
ddrescue -r 3 /dev/sdc3 backup2.img
```

backup2 is 580 G and ext4 so I mount the finished image:

```
mount -t ext4 -o loop backup2.img /media/backup2
```

Killed

I click to mount and view the new backup that has appeared on the left nautilus screen and I receive the error:  loop device busy.

so to list the loop devices I have mounted

```
sudo losetup -a

skynet@skynet-desktop:~$ sudo losetup -a
/dev/loop0: [0812]:39887697 (/home/skynet/backup2.img)
/dev/loop1: [0812]:39887697 (/home/skynet/backup2.img)
```

```
sudo losetup -d /dev/loop1
loop: can't delete device /dev/loop1: Device or resource busy
```

okay maybe its stuck mounting lets try manually unmounting it

```
skynet@skynet-desktop:~$ umount /dev/loop1
umount: /dev/loop1 is not mounted (according to mtab)
```

What am I doing wrong here?  How do I umount / mount a drive when it's stuck in "busy".

---

### Post by wildmanne39 on 2011-05-18
> **Blaze247 said:**
> A removable internal hard drive was refusing to mount:

 ```
mount -t ext4 /dev/sdc3 /media/backup
```

did nothing. no error no prompt.  When attempting to mount through the disk utility it only caused a loading symbol to get stuck on the partition box.  

The drive is healthy and the data is valuable. I don't know what's going on with the mount so I used ddrescue to back up the partition to an image. I followed the instructions here [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


```
ddrescue -r 3 /dev/sdc3 backup2.img
```

backup2 is 580 G and ext4 so I mount the finished image:

```
mount -t ext4 -o loop backup2.img /media/backup2
```

Killed

I click to mount and view the new backup that has appeared on the left nautilus screen and I receive the error:  loop device busy.

so to list the loop devices I have mounted

```
sudo losetup -a

skynet@skynet-desktop:~$ sudo losetup -a
/dev/loop0: [0812]:39887697 (/home/skynet/backup2.img)
/dev/loop1: [0812]:39887697 (/home/skynet/backup2.img)
```

```
sudo losetup -d /dev/loop1
loop: can't delete device /dev/loop1: Device or resource busy
```

okay maybe its stuck mounting lets try manually unmounting it

```
skynet@skynet-desktop:~$ umount /dev/loop1
umount: /dev/loop1 is not mounted (according to mtab)
```

What am I doing wrong here?  How do I umount / mount a drive when it's stuck in "busy".
Hi, if it is busy restart to stop the process but I am not sure that is your only problem, usually you get permission denied problems.

---

