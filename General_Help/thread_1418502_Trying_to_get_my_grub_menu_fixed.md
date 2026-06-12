---
title: "Trying to get my grub menu fixed"
date: 2010-02-28
forum: General Help
---

### Post by coubury on 2010-02-28
HI there.

I installed Ubuntu 9.10 and then xp after and xp has wiped out my grub menu.

I used Gparted to delete the xp partion but when i boot up my pc its says 'operating system cannot be found' (probably trying to find the xp os.

Now , I have booted into ubuntu live cd and im trying to get my old ubuntu grub menu back

Gparted says its still sda1 

I try to install grub but get this error.

Can anyone help?


```
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 241 not upgraded.
Need to get 0B/903kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 118835 files and directories currently installed.)
Removing grub-pc ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ 

```

---

### Post by coubury on 2010-02-28
I have now install grub

my question now is, How do i get my old grub menu back?

---

### Post by spiky001 on 2010-02-28
If it,s not dual boot "just buntu" you dont get the grub menu, i think if you press escape during boot it will show, some1 will correct me if i,m wrong

---

