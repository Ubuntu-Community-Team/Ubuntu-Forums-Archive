---
title: "General error mounting filesystems"
date: 2010-04-01
forum: General Help
---

### Post by frkdavid on 2010-04-01
Hello,

My ubuntu stops when mounting system hdd.
The screen display the following messages :

mountall:/etc/fstab: No such file or directory
fsck from util-linux-ng 2.16
WARNING: couldn't open /etc/fstab: No such file or directory
init: mountall main process (545) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
udevd[560]: can not read '/etc/udev/rules.d/z80_user.rules.
Ubuntu: clean, 474879/24231936 files/28016581/96898047 blocks
root@i7:~# exit_

I suspect the disk manager pysdm that i had just installed today and it had crash during the previous session.

The /etc/fstab file does not exist anymore and i cant rename the fstab.bak because the disk is read-only even for my root user !

I don't know how to exit from that bad situation... I need your help !

Thank you for your help (and sorry for my english)

frank

Ubuntu 9.10

---

### Post by frkdavid on 2010-04-01
I've found a way to escape from this.
I've boot from a CD and rename my /etc/fstab.bak in /etc/fstab
I've restarted the computer and it has work again
I've removed pysdm

frk

---

