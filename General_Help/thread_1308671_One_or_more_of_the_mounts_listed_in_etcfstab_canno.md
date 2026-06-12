---
title: "One or more of the mounts listed in /etc/fstab cannot yet be mounted"
date: 2009-10-31
forum: General Help
---

### Post by louisnerys on 2009-10-31
I was upgrading to karmic, then an error occurred. Now, when I try to turn my computer on, appears the following error:

**[b]one or more of the mounts listed in /etc/fstab cannot yet be mounted**[/b]

I removed all items on fstab and the error persists. Can't run dpkg --configure, it returns that was impossible, the file system was read-only. I tryed fsck also, but there was no problem.

---

### Post by coulhaus on 2009-11-02
Exactly the same thing happened to me, I can't get past this error at all, please help.

---

### Post by rgrig on 2009-11-02
What is the output of:
```
cat /etc/fstab
ls /dev/disk/by-uuid
mount
```
?

---

### Post by coulhaus on 2009-11-02
> **rgrig said:**
> What is the output of:

```
cat /etc/fstab

[B]# <file system>  <mount point>    <type>    <options>    <dump>    <pass>
proc                      /proc                    proc          defaults         0                0
# /dev/sda1
UUID=xxx1 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda2
UUID=xxx2 none swap sw 0 0[/B]

ls /dev/disk/by-uuid

[B]xxx3          xxx1
[/B][B]xxx2          xxx4

[/B] mount

[B]/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
carrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620_
fusectl on /sys/fs/fuse/connections type fusectl (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)[/B]


```

---

### Post by pmorton on 2009-11-02
I confirm the same problem. What is worse, the root recovery shell that is presented to me is useless, as the file system comes up 'read-only' Is this related to an encrypted directory in the user's home directory?

---

### Post by slakkie on 2009-11-02
Hi, please have a look here

[http://ubuntuforums.org/showthread.php?t=1301766](http://ubuntuforums.org/showthread.php?t=1301766)

---

### Post by coulhaus on 2009-11-02
> **pmorton said:**
> I confirm the same problem. What is worse, the root recovery shell that is presented to me is useless, as the file system comes up 'read-only' Is this related to an encrypted directory in the user's home directory?

Yes, I had the same problem with the recovery shell being read only so I used Knoppix to edit the fstab file but even when I comment all the entries out it still halts on this error.

Knoppix was also able to mount all the drives normally so I know it's not a hardware issue.

---

### Post by alphaniner on 2009-11-02
In recovery console, try to remount / read/write with

```
mount -o remount,rw /
```

---

### Post by coulhaus on 2009-11-02
> **alphaniner said:**
> In recovery console, try to remount / read/write with

```
mount -o remount,rw /
```

Yes, that worked and I was then able to run dpkg to complete the upgrade.

Nice one, thanks.

---

### Post by plunder on 2009-11-02
Ever since I upgraded through Update Manager, the day after release, I'm getting the "One or more of the mounts listed in /etc/fstab cannot yet be mounted" thing. Everything boots normally, it seems as though everything is fine.. here is the ```
cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
i'm interested in correcting it, anyone have any ideas where the problem is?

ubuntu 9.04 64-bit -> ubuntu 9.10 64-bit
filesystem: ext3

---

### Post by The_BB on 2009-11-03
I have exactly the same problem as the previous poster. Same fstab.

---

### Post by Defrector on 2009-11-03
I am in the same situation and am fairly confident it is caused by an incomplete upgrade, thus a lot of packages are not upgraded nor configured.

After using:
```
mount -o remount,rw /
```

I got write-access in the minimal shell, which allows to snoop around and fix things. I then did this:
```
apt-get -f install
dpkg --configure --pending
```

...this told me I had over 400 packages not yet installed (!!) and it attempted to fix things. It got somewhat far but I am stuck on an error which says "/var/lib/binfmts does not exist" and a domino effect of dpkg errors follow this resulting in an abort.

It makes some sense: if some packages are new and some are old they may not play nice together and cause a train-wreck at boot, resulting in odd errors like the one in this thread. Networking is broken too; it's going to be a long night.

---

### Post by Defrector on 2009-11-03
An update. If you get a "too many errors" abort with dpkg or apt-get try:
```
dpkg --configure --pending --abort-after=99999
```

This got my system partially bootable. Also consider replacing "--pending" with "-a" as this would theoretically redo the entire config process in case something got nasty by chance last time.

This is going to be my last post in this thread as my additional issues are outside this scope, unless there is a reason to do otherwise.

---

### Post by plunder on 2009-11-06
> **The_BB said:**
> I have exactly the same problem as the previous poster. Same fstab.

im stilling looking for a solution, let me know if you find one, ill do the same :D

---

### Post by beattyrp on 2009-11-06
Can anyone outline a solution to this for someone who isn't a UBUNTU wizard? Computer hangs during boot and displays the error message about /etc/fstab. I tried reinstalling, to a separate partition or to an empty second hard drive, but always get the same error message. Both those installs seemed to complete so I don't think there is any issue with an incomplete install.

---

### Post by flowerdealer on 2009-11-06
I have the same problem here.

---

### Post by plunder on 2009-11-07
i have moved my issue to a new thread, if you get the One or more of the mounts listed in /etc/fstab error on boot, and you still boot in normally, please view and post a reply on:

[http://ubuntuforums.org/showthread.php?p=8267664#post8267664](http://ubuntuforums.org/showthread.php?p=8267664#post8267664)

---

