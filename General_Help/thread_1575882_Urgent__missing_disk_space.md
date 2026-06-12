---
title: "Urgent : missing disk space"
date: 2010-09-16
forum: General Help
---

### Post by ymahe on 2010-09-16
Hi,
i have a Ubuntu 8.04.4 LTS desktop running as server.
I have lost 70 Gb of disk space and I don't find any file to delete to recover some space.

I spend 2 days googling but nothing resolve my problem. I have tried many solutions like reboot, apt-get clean, find files > 1 Gb, ...

NOTHING and it's a semi-production server.

[FONT="Courier New"]# df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda6             219G  208G  150M 100% /
varrun                497M  248K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M   68K  497M   1% /dev
devshm                497M     0  497M   0% /dev/shm
lrm                   497M   40M  458M   8% /lib/modules/2.6.24-25-generic/volatile

# df -i
Sys. de fich.            Inodes   IUtil.  ILib. %IUti. Monté sur
/dev/sda6            14442496 2215159 12227337   16% /
varrun                127144      72  127072    1% /var/run
varlock               127144       3  127141    1% /var/lock
udev                  127144    3025  124119    3% /dev
devshm                127144       1  127143    1% /dev/shm
lrm                   127144      19  127125    1% /lib/modules/2.6.24-25-generic/volatile

# du -h --max-depth=1 /
......
5,3M    /bin
54M     /boot
80K     /dev
18M     /etc
130G    /home
407M    /lib
16K     /lost+found
4,0K    /mnt
4,0K    /opt
7,0M    /root
7,0M    /sbin
4,0K    /srv
0       /sys
2,1G    /usr
2,6G    /var
135G    /


#  lsof | grep deleted
init         1        root    0u      CHR        5,1                  588 /dev/console (deleted)
init         1        root    1u      CHR        5,1                  588 /dev/console (deleted)
init         1        root    2u      CHR        5,1                  588 /dev/console (deleted)

#  lsof | grep tmp
Xorg      6286        root    1u     unix 0xf0c008c0                15194 /tmp/.X11-unix/X0
Xorg      6286        root    9u     unix 0xf0d858c0                15396 /tmp/.X11-unix/X0
Xorg      6286        root   10u     unix 0xf0d7d700                15431 /tmp/.X11-unix/X0
Xorg      6286        root   11u     unix 0xf0d7da80                15445 /tmp/.X11-unix/X0
apache2   6371        root    8u     unix 0xf0d01c40                15387 /tmp/.6371.0.1.sock
apache2   6456        zope    8u     unix 0xf0d01c40                15387 /tmp/.6371.0.1.sock[/FONT]

Thanks for your help
Yves

---

### Post by tx42 on 2010-09-16
i asked similar question and got no response. all i can say is that do a reboot and it will be fixed, for a few days at least...

---

