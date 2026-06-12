---
title: "*help* Urgent Error In Terminal!"
date: 2006-02-24
forum: General Help
---

### Post by bmwboy on 2006-02-24
I got this dpkg error when trying to remove fglrx:
dpkg: unexpected EOF in diversions [ii]
E: Sub-process /usr/bin/dpkg returned an error code (2)

Here is the full terminal...

brandon@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

brandon@ubuntu:~$ sudo su
Password:
Sorry, try again.
Password:
root@ubuntu:/home/brandon# dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200602241534
root@ubuntu:/home/brandon# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

root@ubuntu:/home/brandon# apt-get remove xorg-fglrx-driver
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-fglrx-driver
root@ubuntu:/home/brandon# apt-get remove xserver-fglrx-driver
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-fglrx-driver
root@ubuntu:/home/brandon# sudo rm -rf /usr/share/fglrx
root@ubuntu:/home/brandon# gedit /var/lib/dpkg/diversions

(gedit:9426): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
- using device default
- using device default
root@ubuntu:/home/brandon# apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: xserver-xorg
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu:/home/brandon# apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xserver-xorg
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/274kB of archives.
After unpacking 717kB of additional disk space will be used.

Preconfiguring packages ...
dpkg: unexpected EOF in diversions [ii]
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@ubuntu:/home/brandon# apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 21.9MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: unexpected EOF in diversions [ii]
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by xhie on 2006-02-24
I have no idea what your error is, but I have a question..

Why do sudo su? Instead of just su? does it behave in a differnt way or something then just normal su?

---

### Post by lamego on 2006-02-24
You don't need to manully remove the files, you made a typo on your remove command:
> root@ubuntu:/home/brandon# apt-get remove **xserver-fglrx-driver**
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xserver-fglrx-driver

> root@ubuntu:/home/brandon# apt-get install **xorg-driver-fglrx**
Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.

Remove the correct package which now you have broken ...

---

