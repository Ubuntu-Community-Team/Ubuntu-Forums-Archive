---
title: "External HD - cannot add, del, mod - everything Read-only file system"
date: 2006-06-18
forum: General Help
---

### Post by skyboy on 2006-06-18
Hi,

I have a LACIE 250 firewire external HD, after fresh dapper install, no problem, could use the HD without any problems. 
Then I upgrade KDE 3.5.3, dunno exactly if it is the reason though, but now i cannot use it at all : cannot add files, cannot remove .. cannot do anything, tells me for example.
mkdir: cannot create directory `/media/sdb6/Music/Linkin Park/Meteora/': Read-only file system

Konqueror also say, cannot create directory. Basta !

So what is wrong ?? I'm a 6 years Linux user and yet I tried "chown -R <user> /media/sdb6" and " chmod -R 777 /media/sdb6" and nothing works !
the output of cat /etc/mtab
/dev/sdb6 /media/sdb6 hfsplus rw,noexec,nosuid,nodev,uid=1000,gid=1000 0 0


PLEASE HELP ! all my files for work are in the HD and I need to modify them !!

thanks

---

### Post by skyboy on 2006-06-18
[QUOTE=skyboy]Hi,

I have a LACIE 250 firewire external HD, after fresh dapper install, no problem, could use the HD without any problems. 
Then I upgrade KDE 3.5.3, dunno exactly if it is the reason though, but now i cannot use it at all : cannot add files, cannot remove .. cannot do anything, tells me for example.
mkdir: cannot create directory `/media/sdb6/Music/Linkin Park/Meteora/': Read-only file system

Konqueror also say, cannot create directory. Basta !

So what is wrong ?? I'm a 6 years Linux user and yet I tried "chown -R <user> /media/sdb6" and " chmod -R 777 /media/sdb6" and nothing works !
the output of cat /etc/mtab
/dev/sdb6 /media/sdb6 hfsplus rw,noexec,nosuid,nodev,uid=1000,gid=1000 0 0


PLEASE HELP ! all my files for work are in the HD and I need to modify them !!

thanks[/QUOTE]

Up please !!

---

### Post by PriceChild on 2006-06-18
May be a silly suggestion... but i regularly fix problems by just using the disks admin and unmounting then remounting it.

Pricey

---

### Post by skyboy on 2006-06-19
[QUOTE=PriceChild]May be a silly suggestion... but i regularly fix problems by just using the disks admin and unmounting then remounting it.

Pricey[/QUOTE]

yea, I tried few times all that but dunno, nothing works. thanks anyway.
Please help, I am at work now and cant use my files !! it sucks

---

