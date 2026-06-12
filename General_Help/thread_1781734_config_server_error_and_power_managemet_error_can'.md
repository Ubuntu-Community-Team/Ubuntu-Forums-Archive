---
title: "config server error and power managemet error can't login"
date: 2011-06-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-13
edit:
almost solved read post 3 and 5
-------------------------------------------------------------
i just added a SSD
[http://ubuntuforums.org/showthread.php?t=1780616](http://ubuntuforums.org/showthread.php?t=1780616)
moved sda to sdb
and added my SSD as sda

moved my /var and /tmp to a separate partition 
fixed grub
[http://ubuntuforums.org/showthread.php?t=1781716](http://ubuntuforums.org/showthread.php?t=1781716)

now 
have this issue booting

i got a error message saying
"there is a problem with the configuration server
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"
then i get a login screen with a incorrect theme
then there is a message about a power management issue
edit: see post 4 for solution for this part

---

### Post by pqwoerituytrueiwoq on 2011-06-13
just tried this 
sudo chmod 755 /var/lib/gconf/debian.mandatory/
from [http://forums.debian.net/viewtopic.php?f=6&t=52862&p=304543&hilit=%2Fusr%2Flib%2Flibgconf2+4%2Fgconf+sanity+check+2#p304543](http://forums.debian.net/viewtopic.php?f=6&t=52862&p=304543&hilit=%2Fusr%2Flib%2Flibgconf2+4%2Fgconf+sanity+check+2#p304543)
did not work
edit tried 
chmod 1777 /tmp 
from [http://ubuntuforums.org/showthread.php?t=1061084](http://ubuntuforums.org/showthread.php?t=1061084)
did not work

---

### Post by pqwoerituytrueiwoq on 2011-06-14
i deleted the content of my original /tmp and /var folders
an error occurred while mounting /var/run
an error occurred while mounting /var/lock
still have config error
i feel like running somewhere to scream
and why is it every time you type you it end up yuo (of course the one time you try it ends up correct)

---

### Post by pqwoerituytrueiwoq on 2011-06-14
seems 
chmod 1777 /tmp 
had to be run from the install not a chroot live cd
i stopped gdm and started it after running it and i was able to login correctly
hope everything works on reboot

---

### Post by pqwoerituytrueiwoq on 2011-06-14
at least i can login now
during boot
an error occurred while mounting /var/run
an error occurred while mounting /var/lock
```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=31291866-5557-4805-b357-b504685e2cf7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=afad817b-8d0e-4a98-8202-81cb3161b490 none            swap    sw              0       0
# /var was on /dev/sdb1 during installation
UUID=816d7750-19ba-4440-9248-007356f4770c /var            ext4    defaults        0       0
# /tmp was on /dev/sdb6 during installation
UUID=b04edde4-d0e1-4d41-88e4-19943fa3d1e0 /tmp            ext4    defaults        0       0
# ram disk
tmpfs /home/chad/Desktop tmpfs size=60M,nr_inodes=10k,mode=777 0 0
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs size=65M,nr_inodes=10k,mode=777 0 0

```should it be "defaults        0       2" or "defaults        0       0" for tmp and var partitions?
```
ls -al /var
total 80
drwxr-xr-x 17 root root   4096 2011-06-13 22:36 .
drwxr-xr-x 25 root root   4096 2011-06-13 20:15 ..
drwxr-xr-x  2 root root   4096 2011-06-14 00:15 backups
drwxr-xr-x 18 root root   4096 2011-04-13 07:10 cache
drwxrwxrwt  2 root root   4096 2010-04-13 16:52 crash
drwxr-xr-x  3 root root   4096 2011-04-21 11:48 games
drwxr-xr-x 71 root root   4096 2011-06-13 22:33 lib
drwxrwsr-x  2 root staff  4096 2010-04-23 06:23 local
drwxrwxrwt  3 root root   4096 2011-06-14 00:49 lock
drwxr-xr-x 16 root root   4096 2011-06-14 00:49 log
drwx------  2 root root  16384 2011-06-13 20:23 lost+found
drwxrwsr-x  2 root mail   4096 2011-06-14 01:00 mail
drwxr-xr-x  2 root root   4096 2011-02-11 08:04 opt
drwxr-xr-x 19 root root   4096 2011-06-14 00:49 run
drwxr-xr-x  8 root root   4096 2011-04-16 23:09 spool
drwxrwxrwt  2 root root   4096 2011-06-12 06:48 tmp
drwxr-xr-x  6 root root   4096 2011-06-05 10:43 www
```

---

