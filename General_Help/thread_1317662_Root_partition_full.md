---
title: "Root partition full"
date: 2009-11-06
forum: General Help
---

### Post by fatdunky on 2009-11-06
Hi Guys,

My root partition is full, unfortunately I cant figure out what the hell is taking up the space!?.

I've emptied the trash , run sudo apt-get autoclean and apt-get clean. And from the command output below the biggest directory i can see is 2g? and i have 18g space?

I did have something wierd happen before i noticed this, i accidently mounted one of my hdds with an incorrect uuid and i copied 26g worth of stuff to it, then i realised and mounted it correctly? no idea where those files have gone now, and i cant remeber the uuid i used and i can find any uuids that arnt mounted.

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb6             19228276  18123260    128268 100% /
varrun                 1030740       372   1030368   1% /var/run
udev                   1030740       184   1030556   1% /dev
tmpfs                  1030740       184   1030556   1% /dev/shm
/dev/sdb7             92339048  30634492  57013980  35% /home
/dev/sdd5            961432040 341010792 571583252  38% /media/New_Emule2
/dev/sdc5            961432040 437089644 475504400  48% /media/New_Emule
/dev/sde1            976760032 897621836  79138196  92% /media/Expansion Drive


sudo du -kx --max-depth=1 / | sort -n
0    /dev
0    /proc
0    /sys
4    /home
4    /mnt
4    /opt
4    /selinux
4    /srv
16    /lost+found
44    /media
1812    /root
6220    /bin
6988    /tmp
8560    /sbin
13988    /etc
100124    /boot
294708    /var
425576    /lib
2629368    /usr
3487432    /

sudo du -sk /* 2>/dev/null | sort -n
0    /cdrom
0    /initrd.img
0    /initrd.img.old
0    /proc
0    /sys
0    /vmlinuz
0    /vmlinuz.old
4    /mnt
4    /opt
4    /selinux
4    /srv
4    /xorg.conf.new
16    /lost+found
368    /dev
1812    /root
6220    /bin
6988    /tmp
8560    /sbin
13988    /etc
100124    /boot
295084    /var
425576    /lib
2629368    /usr
30446280    /home
1675147795    /media
fatdunky@marks-linux:/$

---

### Post by michy99 on 2009-11-06
Unmount the disk that you copied to while mounted incorrectly. Look in the directory that it mounts to. The files you see were copied to the mountpoint, but on the root partition because the disk was not mounted.

---

### Post by fatdunky on 2009-11-06
Lol, worked like a charm. Thanks for that =)

---

