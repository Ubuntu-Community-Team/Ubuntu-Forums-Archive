---
title: "ubuntu 12.04 freezes - stopping system V runlevel compatibility"
date: 2012-05-29
forum: General Help
---

### Post by eldafani on 2012-05-29
Hello,

My ubuntu 12.04 crashes constantly, the screen freezes, turns a bit gray and then goes back to normal, but sometimes the desktop panels disappear and when I try to restart I get the message:

Stopping System V runlevel compatibility 
[ 362.424101] end_request: I/O error, dev sda, sector 117508504
[ 362.424395] EXT4-fs (sda1): previous I/O error to superblock detected
[ 362.424593] end_request: I/O error, dev sda, sector 2048
[ 362.424704] Buffer I/O error on device sda1, logical blocl 0
[ 362.424842] EXT4-fs error (device sda1): ext4_find_entry: 935: inode # 3670124: comm sh: reading directory lblocl 0

I have to shut down my laptop manually. Then restarting is problematic, sometimes I get the message "No operating system", sometimes just a black screen, and sometimes it starts.

I have tried different things like switching from gnome-classic to unity, removing/activating broadcom wireless drivers, removing/activating nvidia graphic drivers but the problem persists. 

Any advice is greatly appreciated.

Thanks,
Daniel

---

### Post by dcstar on 2012-05-29
> **eldafani said:**
> Hello,

My ubuntu 12.04 crashes constantly, the screen freezes, turns a bit gray and then goes back to normal, but sometimes the desktop panels disappear and when I try to restart I get the message:

Stopping System V runlevel compatibility 
[ 362.424101] **end_request: I/O error, dev sda**, sector 117508504
[ 362.424395] EXT4-fs (sda1): previous I/O error to superblock detected
[ 362.424593] end_request: **I/O error**, dev sda, sector 2048
[ 362.424704] **Buffer I/O error on device sda1**, logical blocl 0
[ 362.424842] EXT4-fs error (device sda1): ext4_find_entry: 935: inode # 3670124: comm sh: reading directory lblocl 0
..........
Any advice is greatly appreciated.

Thanks,
Daniel

You have a faulty disk. Replace it.

---

