---
title: "deleted libc.so.6 by mistake and now in a soup!"
date: 2010-03-29
forum: General Help
---

### Post by anirvana on 2010-03-29
Hello all,
          I was trying to sort out some problems I was having with synaptic and in a <sarcasm>slash of brilliance</sarcasm> I renamed my libc.so.6 to something else. Since then any command I type throws up:

```

apt-get: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

```

I can't get anything done. Nautilus/package manager/nothing fires up.

Any suggestions :-)

Thanks,
-A

---

### Post by sisco311 on 2010-03-30
/lib/libc.so.6 is a symbolic link to /lib/libc-z.xx.y.so (where z.xx.y is the version number, on my system is libc-2.11.1.so). Boot a Live CD, mount the root partition and create the symbolic link.

Type:
```
sudo fdisk -l
```
(that's a lowercase L in the command) 
and/or
```
sudo blkid
```
to find the device name of the partition (i.e. /dev/sda1).

Mount it:
```
sudo mount /dev/sda1 /mnt
```

Change the current working directory:
```
cd /mnt/lib
```

Find the version number of the target:
```
ls -al libc-*
```

Create the symbolic link:
```
sudo ln -s -T libc-z.xx.y.so libc.so.6
```
(replace z.xx.y with the actual number).

Now you can reboot or chroot in the installation to test it if it worked.

To chroot, mount the virtual filesystems:
```
for i in dev dev/pts proc sys etc/resolv.conf; do sudo mount /$i /mnt/$i; done
```

chroot into Ubuntu:
```
sudo chroot /mnt bash
```

and run:
```
apt-get update
```

if the command works, then you are done, exit from the chroot & reboot:
```
exit
sudo reboot
```

---

