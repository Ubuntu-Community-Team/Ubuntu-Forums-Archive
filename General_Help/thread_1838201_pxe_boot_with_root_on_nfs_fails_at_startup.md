---
title: "pxe boot with root on nfs fails at startup"
date: 2011-09-03
forum: General Help
---

### Post by highcourter on 2011-09-03
for setup pxe server and a diskless client I followed:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
  and
[http://www.felipe-alfaro.org/blog/2007/12/09/configuring-a-diskless-ubuntu/](http://www.felipe-alfaro.org/blog/2007/12/09/configuring-a-diskless-ubuntu/)

I'm doing with dnsmasq. Instead of a ubuntu-client I did use a lubuntu installation. I did setup first a full lubuntu installation on the client's harddisk and from this installation I could verify that dnsmasq issues the right IP, I can download pxelinux.0 from tftp and I can mount /nfsroot from server without any problem.

both server and client use ubuntu-server/lubuntu in version 11.04

when it comes to startup by netboot the bootup sequence stops at...

```

md: ... autorun DONE.
VFS: Cannot open root device "(null)" or unknown-block(8,1)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
Pid: 1, comm: swapper Not tainted 2.6.38-8-generic #42-Ubuntu

```(...)

pxelinux.cfg/default looks like:
```

LABEL linux
DEFAULT vmlinuz-2.6.38-8-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.38-8-generic nfsroot=192.168.2.10:/nfsroot ip=dhcp rw

```/etc/exports
```

/nfsroot        *(rw,no_subtree_check,no_root_squash,async,insecure)

```/nfsroot/etc/fstab
```

proc            /proc           proc    defaults        0       0
/dev/nfs        /               nfs     defaults        0       0
none            /tmp            tmpfs   defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs   defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0

```searching and trying for days... some state, that kernel is not having NFS-options. But I did change BOOT=nfs and MODULES=netboot in /etc/initramfs-tools/initramfs.conf but however left NFSROOT=auto before I did execute update-initramfs.

Any idea how to get things working like this?
If there should be missing any information, let me know please...

thx,
thomas

---

### Post by highcourter on 2011-09-03
for a test I tried to change APPEND line in /tftpboot/pxelinux.cfg/default...
I can write whatever I want there... always get still the same at startup. This make me thin, that this APPEND line is not correctly processed. I added for example raid=noautodetect but at startup it still does "Autodetecting RAID arrays"... does that mean something to someone :confused:

---

### Post by highcourter on 2011-09-03
I got one step further now. Posting here  this information as others might run into same (well maybe nobody as strange-minded as I am though)...

a change in pxelinux.cfg/default to:
```

PROMPT 0
DEFAULT linux root=/dev/nfs nfsroot=192.168.2.10:/nfsroot
APPEND root=/dev/nfs nfsroot=192.168.2.10:/nfsroot
LABEL linux
  KERNEL vmlinuz-2.6.38-8-generic
  APPEND root=/dev/nfs initrd=initrd.img-2.6.38-8-generic nfsroot=192.168.2.10:/nfsroot ip=dhcp rw

```

did now regard the APPEND information in this file. For me at least the one from the HOWTO did not work at all.

---

