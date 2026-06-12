---
title: "Pxe Booting Tries To Load From /cdrom/"
date: 2012-02-14
forum: General Help
---

### Post by rountrey on 2012-02-14
I've been working on getting a PXE server going, sort of going by [this article (http://www.debian-administration.org/articles/478 ).]("http://www.debian-administration.org/articles/478") I am copying the files from the iso files into /tftpboot/ and creating menus to boot it up. My trouble is coming part way through the boot process on Ubuntu and Kubuntu (so far, no problems with Backtrack or CrunchBang), it comes up trying to load from a CD.
Part way through booting on the screen it says 
```
Begin trying nfs mount -o nolock -o ro 192.168.0.12:/tftpboot/Ubuntu/10.04LTS/32bit/Gnome /cdrom

```

Then continues for a few seconds and then stops at
```
Using CD-ROM mount point /cdrom/
Identifying.. [random set of alphanumeric characters changing every time]

```

Is there a way to prevent it looking for a /cdrom/ device? Here is one of my menus I have set up:

```
LABEL 21
        MENU LABEL Ubuntu 10.04LTS 32bit, Desktop (Gnome interface)
                KERNEL /Ubuntu/10.04LTS/32bit/Gnome/casper/vmlinuz
                APPEND initrd=/Ubuntu/10.04LTS/32bit/Gnome/casper/initrd.lz boot=casper text rootfstype=nfs root=/dev/nfs netboot=nfs nfsroot=192.168.0.12:/tftpboot/Ubuntu/10.04LTS/32bit/Gnome 
        TEXT HELP
                Boot Ubuntu 10.04LTS 32bit, Desktop (Gnome interface)
        ENDTEXT
```

---

### Post by galvatron408 on 2012-02-15
Is there a reason why you need to use NFS? If not, use http. It's much easier.

and by the way, you should use the ubuntu doc. I used it before and it works really well.

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

---

### Post by surfer on 2012-02-22
did you make any progress on that front?

i'm trying to install precise using [FAI]("http://fai-project.org/") and also need /dev/nfs as root device.

the error message is:
```
VFS: cannot open device "nfs" or unknown-block(0,255)
```

---

