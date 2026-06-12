---
title: "Xubuntu 10.4 boot problem"
date: 2012-09-22
forum: General Help
---

### Post by Agent26 on 2012-09-22
Hi there all.
I was wondering if anyone might be able to point me in the right direction on an Xubuntu problem.
Last night I was tinkering about in an attempt to overclock my computer.

I was testing booting in with various different fsb values to find the perfect performance.

All of a sudden my xubuntu 10.4 lts would not boot, infact it's dropping me of into busybox with a message busybox 1.13.3 built in a shell (ash) type help for a list of commands.

Im now totaly stuck and will be very pleased if I can fix it.

I don't think my hard disk is broken but might attempt to boot in a different machine to see.
Thankyou

---

### Post by Agent26 on 2012-09-22
just confirmed the hard disk will not boot on any other
 computer.
I suspect this could be a reinstall.

---

### Post by Agent26 on 2012-09-22
does anyone know if I can save my system with the live cd. 
I have booted that now but cant see it 
helping?

---

### Post by Bashing-om on 2012-09-22
Agent26;

Trials, troubles, and tribulations !

From the live cd ...does GParted see the disk drive partitions ?
from the live cd is there any  output of terminal commands:
```
sudo fdisk -lu
sudo parted -l
```[INDENT]trying to help <==BDQ
[/INDENT]

---

### Post by Agent26 on 2012-09-23
Hi there bashing-om,
Thanks for the help.  I just booted the live cd again and after entering those codes it looks like there is a problem. it shows the disk info but also reports that it is unable to open as the hard disk is opened as read only.

---

### Post by Agent26 on 2012-09-23
sudo fdisk -1

This command says unable to open 1.

---

