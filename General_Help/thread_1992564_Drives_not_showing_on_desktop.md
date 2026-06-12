---
title: "Drives not showing on desktop"
date: 2012-05-31
forum: General Help
---

### Post by zcacogp on 2012-05-31
Chaps, 

A bit of an odd one here. And I can't help but think I am being a bit thick (apologies if so.) I have done some searching on here and can't find the answer yet, although there are some similar questions. 

I'm running Xubuntu (I am used to Ubuntu but can't get on with Unity or Gnome-Shell), and have a number of drives mounted at startup, with fstab. But those that are mounted under /media don't show on the desktop. I've tried looking at pretty much every setting, and while I can see how to make it show (or not show) removable drives, this doesn't make a difference to drives that are mounted in fstab. The drives really are mounted - or appear to be - they are listed in file manager and can be used as normal from there. 

I'll put a copy of my fstab at the end of this post. You'll see that I have two bunches of drives, on two different bits of hardware, some behind /media and some behind /mnt, but neither set show up on the desktop. I have used this fstab file exactly as it is on Ubuntu previously (I copied it from my previous installation) and it worked fine there, so I may be battling a difference between Ubuntu and Xubuntu. 

All help welcomed - thanks. 


Oli. 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=dd3dc8ab-cf01-46af-94c8-87ba002dc575 /             ext3    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda3 during installation
UUID=9aa28448-3ab2-446a-bf6e-c63caaa69e77 none            swap    sw              0       0

# Samsung (older) drive - all mounting behind /mnt

UUID=1d588936-4308-4e8d-9ad8-9c0ba6cf118f /mnt/HelenaS ext4 defaults 0 0
UUID=728c678a-4bf6-4c78-8cb2-30b61d9be26f /mnt/IantheS ext4 defaults 0 0
UUID=52C399D625D0301D                     /mnt/PharmacyS ntfs defaults 0 0

# Hitachi (newer) drive - all mounting below /media

UUID=8642a4da-ebcc-42d6-8578-a46d2d75843b /media/Helena ext4 defaults 0 0 
UUID=2c6d4a49-3311-44ef-8d8b-f297ba425417 /media/Ianthe ext4 defaults 0 0 
UUID=3AAFED7A620FE16A                     /media/Pharmacy ntfs defaults 0 0

#/dev/sr0 /media/cdrom  auto  user,noauto,exec,utf8  0  0
/dev/sr0 /media/dvd  udf,iso9660 defaults,noauto,rw,user   0 0
# /dev/sr0	/media/dvd	udf,iso9660	defaults,noauto,ro,user	0	0


#/dev/sr0   /cdrom  udf,iso9660 defaults,noauto,rw,user   0 0

```

---

### Post by LewisTM on 2012-06-01
There is a fundamental difference between how Xubuntu and Ubuntu treat volumes.

On the desktop, Xfce will show mounted or mountable volumes only if they are NOT mounted in fstab. It treats anything in fstab as internal file system objects that the user can manage him/herself. Xfdesktop will list only "external" volumes that it has control of i.e. can mount, unmount or eject.

So if you want to see your drives on the desktop you have to remove them from fstab, give them nice volume labels, and trust the GVFS subsystem will mount them in /media/<LABEL> (or /media/<UUID> if no label) at your request.

By default those will not be mounted at login, they will show as semi-transparent desktop icons. To have them mounted and ready, add commands like this at startup
```
gvfs-mount -d `readlink -f /dev/disk/by-uuid/<UUID>`
```
or 
```
gvfs-mount -d `readlink -f /dev/disk/by-label/<LABEL>`
```
or
```
gvfs-mount -d /dev/sdb1
```

Cheers!

---

### Post by zcacogp on 2012-06-01
Lewis, 

That's a VERY helpful explanation - thank you very much. 

Therefore I have two further questions; 

1. These drives are shared via Samba. In order for that to happen, they need to be mounted at startup. I guess the answer to that is to run the commands you gave me at startup. 

2. *How* do I run those commands at startup? I presume I don't need to type them into the terminal - there must be a way of automating them? (That may be a really stupid question - sorry!) 


Oli.

---

### Post by LewisTM on 2012-06-01
That's not a stupid question ;)
On the contrary the answer is not simple.
You must know that the gvfs-mount trick may be OK for a workstation but it's not ideal for a server setup. As you suspect, those drives won't be available to Samba at boot time.

GVFS is a service targeted at users, the system (root) can't use it at boot. Assuming you would be sharing the drives while logged in (and thus with the drives mounted), here's what you can do:

1) Share the entire /media. That will work for sure and the mounted drives will become available at login as subdirectories.

2) If you don't want to share all of /media, make a directory (e.g. /export), share it, then create symlinks pointing to some of your drives in /media. For Samba to follow symbolic links, include these lines in the Global section of your /etc/samba/smb.conf 
```
follow symlinks = yes
wide links = yes
unix extensions = no
```
3) OR - what I would do - just stick to your current fstab. If you absolutely want to see your drives on the desktop, use symbolic links. That's the Xfce philosophy: keep the desktop tidy and use symbolic links inside you home folder leading to important locations. Think about it and it begins to make sense. Drives are just containers for information and mount points don't mean much. Symlinks allow you to structure that info and make it available to users in a meaningful way.

---

