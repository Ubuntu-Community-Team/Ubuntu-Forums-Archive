---
title: "auto mount spare internal HD without password?"
date: 2011-08-14
forum: General Help
---

### Post by twistedbydesign on 2011-08-14
I recently installed ubuntu on an old dell. I have the OS installed on an 80GB HD and I have a 500GB drive in the computer as a storage drive. I can see the drive and read and write to it just fine. But before I can I have to mount it and provide my password.
Is there a way to set it so that it's already mounted and ready when I start up the computer? The drive is formatted to FAT32
I'm using Ubuntu 9.10
Thanks in advance.

---

### Post by twistedbydesign on 2011-08-15
The reason I want it to automount is because I plan on using Banshee and having all of my music on this drive but i'd prefer to not have to go through the rigmarole of mounting it and pointing banshee at it whenever I wanna use it. I also have my skydome image saved there and I have to open compiz settings and reselect it after it's mounted every time otherwise it doesnt show.

any suggestions?

---

### Post by Lampi on 2011-08-15
What's with an fstab entry for your spare drive? if you use the mount options "noauto, user" you can mount it without sudo rights. But you will run into problems if this drive is not connected. I'd consider writing an udev rule for this case.

I think the kde filemanager dolphin has some dbus rulesets for mounting external drives, but I haven't looked into this yet.

---

### Post by Morbius1 on 2011-08-15
Please post the output of each of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by twistedbydesign on 2011-08-15
I'll post the output this evening as soon as i get home. Thanks!

---

### Post by twistedbydesign on 2011-08-15
Here's what that gave me





ben@ben-desktop:~$ sudo blkid -c /dev/null
[sudo] password for ben: 
/dev/sda1: UUID="724aeb3b-eee9-48d1-b79d-4368d297cbf1" TYPE="ext3" 
/dev/sda5: UUID="33d49476-c875-40c5-ab61-dad427be063d" TYPE="swap" 
/dev/sdb1: LABEL="" UUID="72A7-057D" TYPE="vfat" 
ben@ben-desktop:~$

---

### Post by cgroza on 2011-08-15
Take a look at MountManager. It's an application for managing partition mount points. Seems to be what you need.

---

### Post by twistedbydesign on 2011-08-16
cgroza,
That definitely seems like what I need, but whenever I apply the changes it doesn't actually change anything. It did make my HD unmountable so I had to reformat it (no biggie since there's nothing important on it yet). 
I'll keep messing with it and report back if I make any progress.
Thanks for the suggestions!

---

### Post by Morbius1 on 2011-08-16
I'll try this one more time in a different way. Please post the output of the following commands:

```
 sudo blkid -c /dev/null
``````
 cat /etc/fstab
``````
 mount
```

---

### Post by twistedbydesign on 2011-08-16
Ah...gotcha. sorry about that. 

```
ben@ben-desktop:~$ sudo blkid -c /dev/null
[sudo] password for ben: 
/dev/sda1: UUID="724aeb3b-eee9-48d1-b79d-4368d297cbf1" TYPE="ext3" 
/dev/sda5: UUID="33d49476-c875-40c5-ab61-dad427be063d" TYPE="swap" 
/dev/sdb1: LABEL="MAXTOR" UUID="4AB3-FBCE" TYPE="vfat" 
ben@ben-desktop:~$ 

```

```
ben@ben-desktop:~$  cat /etc/fstab
UUID=724aeb3b-eee9-48d1-b79d-4368d297cbf1 / ext3 defaults 0 1
UUID=33d49476-c875-40c5-ab61-dad427be063d swap swap sw 0 0
ben@ben-desktop:~$ 

```

```
ben@ben-desktop:~$ mount
/dev/sda1 on / type ext3 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ben/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ben)
ben@ben-desktop:~$ 
```

---

### Post by Morbius1 on 2011-08-16
> /dev/sdb1: LABEL="MAXTOR" UUID="4AB3-FBCE" TYPE="vfat"[1] If you currently have the partition mounted unmount it.

[2] Create a permanent mount point for the partition:
```
sudo mkdir /media/Maxtor
```[COLOR=Blue]*Note: any mount point in /home/user-name or /media will produce an icon on the desktop. If you don't want that to happen mount it somewhere else like /mnt/Maxtor or even /Maxtor.*[/COLOR]

[3] Edit fstab as root:
```
gksu gedit /etc/fstab
```[4] Add the following line at the end of fstab:
```
UUID=4AB3-FBCE /media/Maxtor vfat utf8,umask=000,uid=1000 0 2
```[COLOR=Blue]*Note: "uid=1000" will make you the owner of the mounted partition and "umask=000" will give r/w permissions to everyone.*[/COLOR]

[5] Save fstab and back in the terminal run the following command which will test for errors and mount the partition without a reboot:
```
sudo mount -a
```

---

### Post by twistedbydesign on 2011-08-16
That did the trick! Thanks for your help!

---

