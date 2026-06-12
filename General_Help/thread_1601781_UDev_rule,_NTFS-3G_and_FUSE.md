---
title: "UDev rule, NTFS-3G and FUSE"
date: 2010-10-20
forum: General Help
---

### Post by al2cane on 2010-10-20
Hi folks,

I am trying to configure my home ubuntu install so that I can plug and unplug my USB hard drive, whilst Samba will always share it properly across the network with full rw access. I think I've nearly got it setup, but am failing at the last hurdle, hoping some guru here can crack the problem. 

Accomplishing either of these tasks on their own is OK. I can mount the drive using fstab, and sharing works fine across the network, until I unplug and plug back in the drive, which is where I need to manually umount it, and sudo mount -a to get it remounted, or if I remove the fstab entries, ubuntu will mount and umount it when it's unplugged and plugged in, but not with the right privileges (700 , so noone except the logged in user has any rights to it).

I have followed the guide here to setup the udev rule: [http://ubuntuforums.org/showthread.php?t=16822](http://ubuntuforums.org/showthread.php?t=16822), but I believe this guide was written back before ntfs-3g and fuse were updated to make it/them more secure regarding non-root mounting of NTFS file systems.

**/etc/udev/rules.d/10-local.rules**
```

BUS=="usb", SYSFS{product}=="SimpleDrive mini", KERNEL=="sd?1", NAME="My250", SYMLINK="usbdevices/My250",MODE="0666"

```

**/etc/fstab entry:**
```

/dev/usbdevices/My250	/media/My250	ntfs-3g users,auto,rw,exec 0 0 

```

I did try chown root $(which ntfs-3g) and chmod 4755 $(which ntfs-3g), and the current situation I'm in is that the drive is mounting fine at boot time, with the privileges I want it to mount with, but if I unplug and replug the drive I get:

**Error message when I unplug and replug the drive**
```
Error mounting: mount exited with exit code 1: helper failed with:
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at http://ntfs-3g.org/support.html#unprivileged
```

If I manually sudo umount /media/My250, and then sudo mount -a, the drive is umounted and remounted fine, so I'm thinking it has to be down to ntfs-3g/fuse not allowing the currently logged in user (not root) to unmount and then remount it. 
 
I figured I could follow the link, or google the error and find a guide on how to do either of these but I can only find other people with the same problem, being told to do what it says in the error message... but without any instructions, so I'm asking here!

How do I either: 
a) remove the setuid/setgid bit from the binary or
b) rebuild NTFS-3G with integrated FUSE support?

---

### Post by Morbius1 on 2010-10-20
I am so interested in finding the answer to your question ( for reasons other than your own ) that I've been debating with myself to post or not.

Until the guru's answer your question:
> or if I remove the fstab entries, ubuntu will mount and umount it when  it's unplugged and plugged in, but not with the right privileges (700 ,  so noone except the logged in user has any rights to it).There is a samba solution to this problem. If the only user that can access the partition is you then use a mask to make the remote user look like you:
```
force user = you
```Change "you" to your actual login username. 

Where you place that line depends on what method of samba sharing you are using. If it's classic share then it should go in the share definition itself in smb.conf. If you're using Nautilus-share then it should go into the [global] section of smb.conf.

---

### Post by sisco311 on 2010-10-20
You can use an udev rule to mount them with proper permissions:
 [http://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g](http://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g)

EDIT: After the .rules file is created you have to restart udev:
```
sudo udevadm control restart
```then unplug the device and plug it back in.

---

### Post by al2cane on 2010-10-21
> **sisco311 said:**
> You can use an udev rule to mount them with proper permissions:
 [http://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g](http://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g)

EDIT: After the .rules file is created you have to restart udev:
```
sudo udevadm control restart
```then unplug the device and plug it back in.
Replaced my udev rule file with that, and removed my fstab entry, restarted machine and that's worked perfectly. 

The sudo udevadm control restart command didn't work, nor did sudo service udev restart, I had to restart the machine in order to get it done.

> **Morbius1 said:**
> 
There is a samba solution to this problem. If the only user that can access the partition is you then use a mask to make the remote user look like you:
```
force user = you
```Change "you" to your actual login username. 

Where you place that line depends on what method of samba sharing you are using. If it's classic share then it should go in the share definition itself in smb.conf. If you're using Nautilus-share then it should go into the [global] section of smb.conf.
I also tried this and also a perfectly valid solution for what I wanted to do with Samba. I was using classic share. I tried it using Nautilus-share, and it works only if I tick "Guest access" when setting the share AND have force user = myusername in the global section of the smb.conf config. Having only one or the other won't work. 

I can't decide now which to use now, but I'll try both for a while and see which fits best. Thanks for both solutions folks!

---

### Post by Morbius1 on 2010-10-21
> I tried it using Nautilus-share, and it works only if I tick "Guest  access" when setting the share AND have force user = myusername in the  global section of the smb.conf config.That's interesting. I just created a test directory with permissions of 0700 and shared it using Nautilus w/o guest access. After authentication using a different username but using the "force user" parameter I was able to access the directory.

I'll play with this a bit and see if I can reproduce your condition. Anyway I'm glad the guru (sisco311) came along.

---

