---
title: "Persistent mode for PXE netboot"
date: 2010-03-04
forum: General Help
---

### Post by rascal999 on 2010-03-04
I have LiveCD successfully booting over PXE to multiple clients. I would like to be able to make modifications to the OS and I understand this is possible using a [USB stick]("https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence"). I know it is possible to customize Ubuntu by decompressing the squashfs, but I'm looking for quicker alternatives..

I have created a casper-rw file (ext3) in casper/ and have added 'persistent' to the APPEND line in a file under pxelinux.cfg/ Now when the clients download the squashfs, it seems it tries (and fails) to access /dev/fd0. I'm not sure if this is a result of adding 'persistent' after boot=casper. I'm hoping someone can come up with a netboot equivalent of modifying a LiveCD squashfs, as I am stuck here.

Thanks! :)

---

### Post by rascal999 on 2010-03-05
I made the filesystem ext2 and now I can edit it from the server

---

