---
title: "mount not responding"
date: 2009-11-03
forum: General Help
---

### Post by yanvolking on 2009-11-03
Hello Community,

I am trying to mount a USB stick (/dev/sdb) or also /media/USB, onto a directory I created especially for that purpose : /home/yan/Desktop/mount.  mount is empty

I run the following command

yan@yan-laptop:~$ sudo mount /dev/sdb /home/yan/Desktop/mount

and get :

mount: /dev/sdb already mounted or /home/yan/Desktop/mount busy

so I run :

yan@yan-laptop:~$ umount /dev/sdb

and I get : 
umount: /dev/sdb is not mounted (according to mtab)

SO IS 7dev/sdb mounted or unmounted????  seems my computer cant make up its mind.  Just to be sure I then run :

yan@yan-laptop:~$ sudo umount /home/yan/Desktop/mount

and get :

umount: /home/yan/Desktop/mount: not mounted

Anyone can tell me what's stopping me from mounting the USB stick into the mount directory?

Thanks


yan@yan-laptop:~$

---

