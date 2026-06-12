---
title: "Separate Home"
date: 2010-04-26
forum: General Help
---

### Post by cmcanulty on 2010-04-26
Well I finally set up my netbook with 2 partitions one for Ubuntu and one for home. However the system treats it as a mounted disk with a mount icon on desktop and all the shortcuts to home point to empty folders and my home I have to navigate to though that mounted disk.Also it isn't picking up all my customizations I had in Home. Is there a way to fix this or should I go back and reinstall to make everything on one partition.Also on an unrelated note with this netbook when I minimize things they disappear on the screen bottom is there a way to minimize to the top panel. I tried the netbook remix earlier and hated the interface. I want it to be as similar as possible to my laptop so I can use grsync to keep everything the same.Thank you

---

### Post by bodhi.zazen on 2010-04-26
Sounds as if your home partition is not configured properly.

What is the ouptput of

```
mount
```
 and

```
grep home /etc/fstab
```

---

### Post by cmcanulty on 2010-04-26
It is difficult to reply because every time I minimize a screen to do the terminal or anything it disappears and I can't find a place it minimizes ```

```this is my 3rd try to post a reply.```
cmcanulty@AcerAspireOne:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cmcanulty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cmcanulty)
/dev/sda2 on /media/a6a0bced-3afe-4c27-bc44-a289c7de5d9a type ext4 (rw,nosuid,nodev,uhelper=devkit)
cmcanulty@AcerAspireOne:~$ 
```cmcanulty@AcerAspireOne:~$ grep home /etc/fstab
cmcanulty@AcerAspireOne:~$

Ok I figured out how to add the minimized stuff though it always just worked before this install but the home is a big problem and I want to either fix it or try another reinstall before I get everything tweaked again.

---

### Post by bodhi.zazen on 2010-04-26
From that output you are not using the partition in question as a separate home partition.

You can either re-install and during the installation process manually specify the partition to be used as /home , or manually move your home partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by cmcanulty on 2010-04-27
OK I reinstalled and got it correct but now it won't read my flash drive or my ext hard drive formatted to ext4 can't see them, or mount them except from live run.

---

