---
title: "Ubuntu Server: Errors with apt-get upgrade or install &lt;something&gt;"
date: 2009-09-16
forum: General Help
---

### Post by studioeng on 2009-09-16
Hi,

I'm really sorry if someone has already posted about this problem; but here goes anyway. I've been running Ubuntu Server 9.04 for a while, I've mostly kept it up to date.

Some time ago when I did either an apt-get upgrade or apt-get install <something> and the server then broke. I cannot do upgrades or install any software using apt-get.

I get the following errors:
```
root@server:~# sudo apt-get install build-essential
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

root@server:~# sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up lilo (1:22.8-7ubuntu1) ...
Running lilo...
Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/volgroup01/logvol01'
Fatal: device-mapper: Sector outside mapped device? (2049: 3019685932/3907026944)
dpkg: error processing lilo (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.28-13-server (2.6.28-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-13-server
ERROR lilo fails for new /boot/initrd.img-2.6.28-13-server:

Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/volgroup01/logvol01'
Fatal: device-mapper: Sector outside mapped device? (2049: 3019828716/3907026944)
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-13-server (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-server:
 linux-restricted-modules-2.6.28-13-server depends on linux-image-2.6.28-13-server; however:
  Package linux-image-2.6.28-13-server is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-13-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-15-server
ERROR lilo fails for new /boot/initrd.img-2.6.28-15-server:

Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/volgroup01/logvol01'
Fatal: device-mapper: Sector outside mapped device? (2049: 3019800580/3907026944)
dpkg: subprocess post-installation script returned error exit status 1
```*(I know sudo is not needed under root user, but I kept it just in case.)*

I've been looking and searching for a few months to fix it, but I'm going round in circles. is there a fix for this, or just a case of reinstalling everything again?

Other than this, the server runs perfectly fine, I just can't install anything or upgrade it.

---

