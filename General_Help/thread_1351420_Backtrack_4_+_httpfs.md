---
title: "Backtrack 4 + httpfs"
date: 2009-12-10
forum: General Help
---

### Post by nagileon on 2009-12-10
Hi there

Backtrack 4  is based on Ubuntu and I'm not getting any response from their forums so I decided to ask here. 

Backtrack 4 is PXE enabled but the way it works doesn't quite satisfy my needs. I already have a PXE server in my network with Ubuntu,Centos,Fedora,Suse,Memtest,Knopix etc.

I need to add backtrack to the list.

So I copied vmlinuz + initrd.gz to /tftpboot/backtrack/
I modified my configuration file: vim /tftpboot/pxelinux.cfg/default

LABEL backtrack
MENU LABEL BT4
KERNEL backtrack/vmlinuz
IPAPPEND 1
APPEND netboot=http httproot=hxxp://10.15.0.3/repo/ vga=0x317 initrd=backtrack/initrd.gz ramdisk_size=9999 root=/dev/ram0 rw quiet

When I boot I can see the initrd.gz and vmlinuz are being loaded but then the system is unable to find BT4 directory and it drops into busybox shell. Which means that hxxp://10.15.0.3/repo/ is not being mounted to /mnt/httpfs/.

I can mount it from command line though: 

httpfs hxxp://10.15.0.3/repo/ /mnt/httpfs/

All this makes me think that backtrack doesn't really understand following line in the configuration file: 

APPEND netboot=http httproot=hxxp://10.15.0.3/repo/

So how to make backtrack aware that I need it to mount httproot=hxxp://10.15.0.3/repo/ to /httpfs during the boot proces ?

Reagrds

Peter

---

