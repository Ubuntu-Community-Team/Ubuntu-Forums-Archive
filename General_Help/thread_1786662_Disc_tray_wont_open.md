---
title: "Disc tray wont open"
date: 2011-06-19
forum: General Help
---

### Post by jameswm on 2011-06-19
Ubuntu wont recognize my disc drive. I installed Ubuntu with Wubi, so I have dual boot. I have the latest Ubuntu. On Windows 7, my disc drive works fine. On Ubuntu, however, the tray wont open. I also tried going to terminal and typed "eject" and "sudo eject" and I receive this message:

eject: unable to find or open device for: `cdrom'

I'm not sure if it has anything to do with it, but when Ubuntu OS starts up, it takes a while and says "ata3 soft reset failed" or something like that. I had to set the delay to last longer so it could start up

---

### Post by jameswm on 2011-06-20
54 views and no responses? Does anyone at all know what's wrong?

---

### Post by DawieS on 2011-06-20
I don't have any experience with a **Wubi** installation, but my guess is that the problem may be caused by having another "layer" on top of which Ubuntu is installed. IMO a **Wubi** install is only useful for trying out Ubuntu. If you like it, my recommendation would be to get rid of the **Wubi** installation, and do a proper installation of Ubuntu on a separate partition or hard drive.:grin:

---

### Post by Grenage on 2011-06-20
I have no Wubi experience, and haven't soon your problem before; now that's out of the way:

Could you post the output of these two commands:

```
eject -n
cat /etc/fstab
```

---

### Post by knubles on 2011-06-20
Could be the /dev is wrong. I had this trouble and had to have an alias to correct it. 
knubles

---

### Post by jameswm on 2011-06-20
> **Grenage said:**
> I have no Wubi experience, and haven't soon your problem before; now that's out of the way:

Could you post the output of these two commands:

```
eject -n
cat /etc/fstab
```

james@ubuntu:~$ eject -n
eject: unable to find or open device for: `cdrom'
james@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by jameswm on 2011-06-20
NO ONE can help? :(

---

### Post by haqking on 2011-06-20
have you tried a unmount ?

sudo umount /dev/cdrom sudo eject /dev/cdrom

and what version of Ubuntu ? I know someone who had same issue with 10.04 when he upgraded to 10.10 the problem went away

what is the output of:

eject -v

---

### Post by jameswm on 2011-06-20
> **haqking said:**
> have you tried a unmount ?

sudo umount /dev/cdrom sudo eject /dev/cdrom

and what version of Ubuntu ? I know someone who had same issue with 10.04 when he upgraded to 10.10 the problem went away

what is the output of:

eject -v

Ubuntu 11.04 Wubi

james@ubuntu:~$ sudo umount /dev/cdrom sudo eject /dev/cdrom
[sudo] password for james: 
umount: /dev/cdrom: not found
umount: sudo: not found
umount: eject: not found
umount: /dev/cdrom: not found

& 

james@ubuntu:~$ eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: unable to find or open device for: `cdrom'

---

### Post by haqking on 2011-06-20
> **jameswm said:**
> Ubuntu 11.04 Wubi

james@ubuntu:~$ sudo umount /dev/cdrom sudo eject /dev/cdrom
[sudo] password for james: 
umount: /dev/cdrom: not found
umount: sudo: not found
umount: eject: not found
umount: /dev/cdrom: not found

& 

james@ubuntu:~$ eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: unable to find or open device for: `cdrom'


As a process of elimination have you tried booting to a 11.04 Live CD to see if works and is recognised ? then you know it is a problem with your install rather than 11.04 itself, if it is not recognised under that then try a nother version like 10.04 LTS just to make sure.

---

### Post by jameswm on 2011-06-20
> **haqking said:**
> As a process of elimination have you tried booting to a 11.04 Live CD to see if works and is recognised ? then you know it is a problem with your install rather than 11.04 itself, if it is not recognised under that then try a nother version like 10.04 LTS just to make sure.

Alright, well, I'm busy packing stuff to move to a new home, so I'll try it out next week when I get some time to sit down with it

---

