---
title: "Samba root directory share with fstab"
date: 2009-08-03
forum: General Help
---

### Post by yanewby on 2009-08-03
I have just bought a new NAS drive and I am trying to work out how to give it full read/write permissions via fstab.

I tried to follow these instructions:
[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)

At present I have this in my /etc/fstab:

//xxx.xxx.x.xxx/volume_1 /media/samba cifs credentials=/etc/samba/user,uid=1000,gid=100,umask=0000,rw  0  0

/etc/samba/user contains my username and password
xxx.xxx.x.xxx/volume_1 is the location of the disk drive

Using these settings I am able to write in certain folders but not in others.  I would like to be able to mimic the behaviour of my home folder in Ubuntu (ie write anywhere on the drive, create any folder or file wherever I want).

Any ideas of how to implement this?

(I am still quite new to Ubuntu but I'm not scared to try anything.  If you need more information or require me to type something in Terminal I will be more than happy if it helps resolve this!).

---

