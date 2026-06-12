---
title: "DD Help"
date: 2012-10-06
forum: General Help
---

### Post by 1Yeoj1 on 2012-10-06
I am trying to put a file on the second sector of a disk ( right after the bootloader) and I was wondering what the dd command would be?

Yeoj

---

### Post by oldfred on 2012-10-06
Grub2 uses sectors after the MBR for core.img. Do not corrupt that data area like a bunch of Windows software does.

HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

---

### Post by 1Yeoj1 on 2012-10-06
I wrote a bootloader and I want to put a homemade kernel right after it on the disk.

Yeoj

---

### Post by oldfred on 2012-10-06
Some info on dd.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by 1Yeoj1 on 2012-10-08
```
sudo dd if=kernel.bin bs=512 skip=1 of=/dev/sdb
dd: `kernel.bin': cannot skip to specified offset
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0116388 s, 0.0 kB/s

```I followed the tutorial and this is what I got back. For calculations the kernel.bin is 2 bytes(for now). 

Yeoj

---

