---
title: "Acidentically removed libdrm-nouveau1"
date: 2010-09-13
forum: General Help
---

### Post by rasmus91 on 2010-09-13
Hi there

Yes, as the title says i kinda screwed up a bit.

I started removing the package through synaptics, even though it told it would render Ubuntu unusable.

I Have inserted a sd card with ubuntu on, and chrooted unto my harddrive.

This is what i've tried so far:
```
root@ubuntu:/# apt-get install libdrm-nouveau1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdrm-nouveau1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up gnome-system-tools (2.30.0-0ubuntu2) ...
/var/lib/dpkg/info/gnome-system-tools.postinst: 6: cannot create /dev/null: Permission denied
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 107, in <module>
    fd = os.open("/dev/null",os.O_WRONLY)
OSError: [Errno 13] Permission denied: '/dev/null'
dpkg: error processing gnome-system-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can see that i do not have permission to change somethings. Is that due to me not being logged in as root on my harddrive?

Anyway, can anyone tell me an easy way to fix this?

The main reason i tried to remove this package was due to my computer spitting out something about the nouveau driver not functioning or something. and i don't really know what i can do about this.

Help is greatly appreciated :)

---

### Post by rasmus91 on 2010-09-13
found the command

```
sudo apt-get install --fix-broken
```

and tried it, but all that happened was this:

```
root@ubuntu:/# sudo apt-get install --fix-broken
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up gnome-system-tools (2.30.0-0ubuntu2) ...
/var/lib/dpkg/info/gnome-system-tools.postinst: 6: cannot create /dev/null: Permission denied
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 107, in <module>
    fd = os.open("/dev/null",os.O_WRONLY)
OSError: [Errno 13] Permission denied: '/dev/null'
dpkg: error processing gnome-system-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by rasmus91 on 2010-09-14
So i went home and tried something different.

```
root@ubuntu:/# sudo apt-get upgrade
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up gnome-system-tools (2.30.0-0ubuntu2) ...
/var/lib/dpkg/info/gnome-system-tools.postinst: 6: cannot create /dev/null: Permission denied
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 107, in <module>
    fd = os.open("/dev/null",os.O_WRONLY)
OSError: [Errno 13] Permission denied: '/dev/null'
dpkg: error processing gnome-system-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i Don't get this... And i really need help to restore my system.

---

### Post by WorMzy on 2010-09-14
When you say that you chrooted into it, did you mount --bind proc, dev and sys first?

e.g.
```
sudo mount -t ext4 /dev/sda1 /mnt
```
```
sudo mount --bind /proc /mnt/proc
```
```
sudo mount --bind /dev /mnt/dev
```
```
sudo mount --bind /sys /mnt/sys
```
```
sudo chroot /mnt
```

---

### Post by rasmus91 on 2010-09-16
Don't think so no.

Thanks for the tip!

I'll write back when I've tried it.

---

