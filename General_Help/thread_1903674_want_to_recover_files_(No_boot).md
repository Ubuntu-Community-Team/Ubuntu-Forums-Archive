---
title: "want to recover files (No boot)"
date: 2012-01-03
forum: General Help
---

### Post by kyawthurein on 2012-01-03
2days ago, I installed Ubuntu 11.10 with Wubi on Windows7.
Everything's fine until **I cant boot after installing Nvidia Graphic driver **which **replaces the old one**. :o

**I have root.disk **to recovery of important files.
I m seriously in need of some lost files. :(

What should I do? I m now browsing web & reading forums, trying to get the files in time.
I need them for my job.
Thanks in advance.

---

### Post by kyawthurein on 2012-01-03
I read some forums and solved myself.. ;)
I made following steps:

1. make my USB stick into "installer for Ubuntu" using unetbootin-windows-563.exe
2. boot from USB stick > live cd no install > Ubuntu starts from USB.
3. open terminal 
a) sudo fdisk -l (to see all disks)
b) sudo mkdir /win (to create "win" folder in "system files" of ubuntu)
c) sudo mount /dev/sdax /win (to mount drive sdax (x refer to drive where root.disk exists) to win)
d) sudo mkdir /vdisk (vdisk folder)
e) sudo "sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk (this makes files in root.disk seen in vdisk folder in system file)

Thanks anyway :D

---

