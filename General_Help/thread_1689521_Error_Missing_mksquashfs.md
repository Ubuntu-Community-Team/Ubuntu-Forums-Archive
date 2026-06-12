---
title: "Error: Missing: mksquashfs"
date: 2011-02-16
forum: General Help
---

### Post by kutchbhi on 2011-02-16
I am trying to install this : [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/) on ubuntu 10.10 

This is the message I get upon attempting to run the script.:

> 6550K .......... .......... .......... .......... .......... 99% 62.5K 1s
  6600K .......... .......... .......... .......... ......... 100% 71.8K=1m40s

2011-02-17 08:40:09 (66.7 KB/s) - `multisystem.tar.bz2.1' saved [6809548/6809548]


bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
lsof: status error on /usr/local/share/multisystem: No such file or directory
lsof 4.81
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
 Error: Missing: mksquashfs 


Any ideas what I can do to fix this ? I couldn't find any package with the name as mksquashfs .

---

