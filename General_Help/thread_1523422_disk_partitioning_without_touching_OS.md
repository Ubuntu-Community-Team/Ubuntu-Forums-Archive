---
title: "disk partitioning without touching OS"
date: 2010-07-03
forum: General Help
---

### Post by ehmdjii on 2010-07-03
hello, i currently have ubuntu server installed, where i host some files. now is it possible to create a new partition on my disk and move the data there, without resintalling the OS?

if so, how?

root@kitsch:~# df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/mapper/kitsch-root
              ext4   237251272  69025564 156174048  31% /
none      devtmpfs      492320       212    492108   1% /dev
none         tmpfs      496904         0    496904   0% /dev/shm
none         tmpfs      496904       324    496580   1% /var/run
none         tmpfs      496904         0    496904   0% /var/lock
none         tmpfs      496904         0    496904   0% /lib/init/rw
/dev/sda1     ext2      233191     33669    187081  16% /boot


thanks a lot!

---

### Post by spiky001 on 2010-07-03
Yes you can use Gparted on the live cd to make a new partition

---

