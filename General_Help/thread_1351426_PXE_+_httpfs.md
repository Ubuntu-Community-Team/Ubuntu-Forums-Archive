---
title: "PXE + httpfs"
date: 2009-12-10
forum: General Help
---

### Post by nagileon on 2009-12-10
Hi there

I have a PXE server in my network with Centos,Fedora,Suse,Memtest,Knopix etc.

I need to add Ubuntu live CD to the list.

So I copied vmlinuz + initrd.gz to /tftpboot/ubuntulcd/
I modified my configuration file: vim /tftpboot/pxelinux.cfg/default

LABEL ubuntulcd
MENU LABEL ULCD
KERNEL ubuntulcd/vmlinuz
IPAPPEND 1
APPEND netboot=http httproot=hxxp://10.15.0.3/repo/ulcd.iso vga=0x317 initrd=ubuntulcd/initrd.gz ramdisk_size=9999 root=/dev/ram0 rw quiet

When I boot I can see the initrd.gz and vmlinuz are being loaded but then the system drops into busybox shell. Which means that hxxp://10.15.0.3/repo/ is not being mounted to /mnt/httpfs/.

I can mount it from command line though: 

httpfs hxxp://10.15.0.3/repo/ /mnt/httpfs/

All this makes me think the system doesn't really understand following line in the configuration file: 

APPEND netboot=http httproot=hxxp://10.15.0.3/repo/

So how can I  make system aware that I need it to mount httpfs=hxxp://10.15.0.3/repo/ to /httpfs during the boot proces ?

Reagrds

Peter

---

### Post by bacardiandwatermelon on 2009-12-10
No idea... but this could help..

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

---

