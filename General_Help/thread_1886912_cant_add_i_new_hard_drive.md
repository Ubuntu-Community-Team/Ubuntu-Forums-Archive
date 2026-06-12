---
title: "cant add i new hard drive"
date: 2011-11-25
forum: General Help
---

### Post by john dou on 2011-11-25
I recently found a 20 Gb hard drive in the garbage. I formate it to ext2 using fdisck and  mkfs. I mount it. Now, when i make the command "df" i get,   

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             75476088  63211196   8430832  89% /
none                    245168       216    244952   1% /dev
none                    250388         4    250384   1% /dev/shm
none                    250388       312    250076   1% /var/run
none                    250388         0    250388   0% /var/lock
none                    250388         0    250388   0% /lib/init/rw
/dev/sdb1             75476088  63211196   8430832  89% /home/andres/disco20GB
/home/andres/.Private
                      75476088  63211196   8430832  89% /home/andres




the new hardrive is /dev/sdb. The /dev/sda is my 80 Gb master hard drive. 
im usin ubuntu server 10.04. Any ideas?

---

### Post by pqwoerituytrueiwoq on 2011-11-25
i would format using gparted my self you will need to update your /etc/fstab file with the uuid on the partition(s) on it as well as mount points

who would throw out a working 20gb hdd they come in handy in a pinch

example fstab line:
UUID=00000000-0000-0000-0000-000000000000 /mnt/storage            ext2    defaults                             0       2

also run *sudo mount -a* after updating the file to mount the hdd without a reboot

---

