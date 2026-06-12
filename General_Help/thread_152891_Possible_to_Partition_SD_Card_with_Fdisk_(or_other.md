---
title: "Possible to Partition SD Card with Fdisk? (or other program)"
date: 2006-03-30
forum: General Help
---

### Post by harrisale on 2006-03-30
I just bought a new 2GB SD Card and I want to partition it into two 1GB parts.

I've tried using Fdisk on /media/usbdisk but it won't let me partition it.

Is it possible at all in any way to partition a Secure Digital Card? Windows wont do it (P.O.S)

btw, I am doing this because my Palm Tungsten E2 will not recognize more than 1GB partitions.

thanx,

=harrisale+

---

### Post by Iandefor on 2006-03-30
[quote=harrisale]I just bought a new 2GB SD Card and I want to partition it into two 1GB parts.

I've tried using Fdisk on /media/usbdisk but it won't let me partition it.

Is it possible at all in any way to partition a Secure Digital Card? Windows wont do it (P.O.S)

btw, I am doing this because my Palm Tungsten E2 will not recognize more than 1GB partitions.

thanx,

=harrisale+[/quote] What're the contents of /etc/mtab? You need to refer to the block device, not the mount point.

---

