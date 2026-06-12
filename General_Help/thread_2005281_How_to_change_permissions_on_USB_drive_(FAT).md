---
title: "How to change permissions on USB drive (FAT)"
date: 2012-06-17
forum: General Help
---

### Post by rdh61 on 2012-06-17
Hi

Having yet ***another*** frustrating problem on 12.04 that did not appear on previous versions.

There are two users using this computer, both with administrator accounts. I have to be able to access and manipulate files on my USB drive through both accounts, yet because of a permissions issue, I can only access it through my own account.

However, when signed in as myself, or even when browsing as root, I am unable to change the permissions on the drive (right click -> properties -> permissions).

Please, how can I change these permissions to allow both accounts to access and use files on this USB drive? The file system is FAT 32.

Many thanks.

---

### Post by mbuell on 2012-06-17
From the command line, using sudo and chmod tends to work better for me when I have a problem. Also, if it is choking for some reason, the command line will give me an error report I can see. 

I apologize that some of the following answer will be somewhat vague. Going from memory.

When you plug a device in - like a thumb drive - if I recall correctly, there are settings that tell it what the default ownership is - but I do not remember where those settings might be. 

Also, you might want to look at the group assignments. You would want both users, AND the device, to be in the same group, with that group automatically having permissions. 

I hope that gives you some leads for further research.

---

### Post by coffeecat on 2012-06-17
You can't change permissions on a FAT32 drive, because FAT32 doesn't support Linux permissions. Permissions are determined by mount options, so we need to look at how the drive is being mounted in each account.

Questions:

1 - Are you allowing the system to automount the USB drive, or have you created an entry in /etc/fstab for this? If the latter, please post the contents of your /etc/fstab file. If you allow the drive to be automounted, do so in each account and then post the output of this terminal command:

```
mount
```

We need two mount outputs, one for each account.

2 - Did you automount the drive in one account and then log out an in to the other account leaving the drive in situ?

3 - Have you installed any apps which allegedly "help" with automounting USB drives? In particular usbmount?

---

### Post by rdh61 on 2012-06-18
> **coffeecat said:**
> 
1 - Are you allowing the system to automount the USB drive, or have you created an entry in /etc/fstab for this? 

Automount. 

```
robert@robert-desktop:~$ mount
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
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
javafs on /home/robert/WualaDrive type fuse.javafs (rw,nosuid,nodev,user=robert)
/dev/sdb on /media/ADATA type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
```

```
eilene@robert-desktop:~$ mount
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
javafs on /home/robert/WualaDrive type fuse.javafs (rw,nosuid,nodev,user=robert)
gvfs-fuse-daemon on /home/eilene/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eilene)
/dev/sdb on /media/ADATA type vfat (rw,nosuid,nodev,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

```

> **coffeecat said:**
> 2 - Did you automount the drive in one account and then log out an in to the other account leaving the drive in situ?

Yes.

> **coffeecat said:**
> 3 - Have you installed any apps which allegedly "help" with automounting USB drives? In particular usbmount?

No.

---

### Post by coffeecat on 2012-06-18
This is your problem:

> **rdh61 said:**
> [QUOTE=coffeecat;12034615]
2 - Did you automount the drive in one account and then log out an in to the other account leaving the drive in situ?
Yes.[/QUOTE]

However, the mount information you provided shows that you did something different this time, namely letting the device be automounted in each account. This:

> **rdh61 said:**
> 

```

/dev/sdb on /media/ADATA type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
```

```
/dev/sdb on /media/ADATA type vfat (rw,nosuid,nodev,uid=1001,gid=1001,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

```


Your ADATA device was correctly mounted from each account. With the first account the mount options include "uid=1000,gid=1000", and from the second "uid=1001,gid=1001", which is to be expected. If, however, you automount the device from your uid=1000 account, leave it mounted, log out and back into the uid=1001 account, you will not be able to access the files because they have been mounted for the account uid=1000 only. Let me illustrate this with a simulation.

I plugged a FAT32 USB flash device into my uid=1000 account in a 12.04 system. It automounted with the same options as you saw. I then copied a text file to it and further edited the text file from the USB device. I then ejected the device and physically removed it, and logged out and back into my second uid=1001 account, after which I re-inserted the USB device. It was mounted with permissions (uid=1001) suitable for my second account and I was able to continue editing the text file (and copy it).

However, if I let the device be automounted while logged into one account and left the device mounted while logging out and into the other account, the device did not appear in the left pane of Nautilus when logged into the second account, nor in the launcher. If I browsed the filesystem -> /media, I could see the USB device mountpoint but was not able to open it, getting a "You do not have the permissions necessary..." message. This is as it should be. If you allow it to be automounted in the account in which you are logged, you should have no problems. The permissions for the files change with the automount options depending on the account you are using. This is as it should be.

All this behaviour is a result of having to set permissions by means of mount options while using Microsoft filesystems, which do not support the Linux/Unix system of permissions and ownership.

---

### Post by rdh61 on 2012-06-18
That explains it perfectly. It behaves as you describe. Solved. Thank you (again).

---

### Post by adroitster on 2012-06-18
> **rdh61 said:**
> That explains it perfectly. It behaves as you describe. Solved. Thank you (again).

Please mark the thread as solved. Thanks !

---

