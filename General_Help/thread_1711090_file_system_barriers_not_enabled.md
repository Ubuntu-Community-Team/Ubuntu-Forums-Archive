---
title: "file system barriers not enabled"
date: 2011-03-20
forum: General Help
---

### Post by RedSquirrel on 2011-03-20
I have an ext3 file system and I would like to enable barriers.

I have added "barrier=1" to the options in **/etc/fstab**: 

```
UUID=#### /  ext3 noatime,errors=remount-ro,barrier=1   0       1
```


but at the end of the boot sequence, Ubuntu 10.10 reports:

**EXT3-fs: barriers not enabled**


I am able to use barriers with ext3 on three other Linux system on this computer (Slackware 13.1, Debian 6.0, and Gentoo).

I wonder if that "barrier=1" setting is filtered out somewhere by Ubuntu. :confused:

Has anyone had any luck using barriers with Ubuntu?

Thanks in advance for any replies.

---

### Post by RedSquirrel on 2011-03-20
I added:

```
rootflags=barrier=1
```to the kernel command line and it works fine now.

(To do that with grub2, see the [grub2 documentation]("https://help.ubuntu.com/community/Grub2"). Edit: To be more specific, look at the information on GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT.)

---

