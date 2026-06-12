---
title: "ATI Driver Installation"
date: 2006-02-27
forum: General Help
---

### Post by jsdewey on 2006-02-27
Alright, I got down to the point where I need install the .deb files:
```
sudo dpkg -i xorg-driver-fglrx_8.22.5-1_i386.deb
sudo dpkg -i fglrx-control_8.22.5-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.22.5-1_i386.deb
```

I have been able to install the kernel-source, but not the others. This is what I get:
```
me@MELINUX-UBUNTU:~/Desktop/Downloads$ sudo dpkg -i fglrx-control_8.22.5-1_i386.deb
(Reading database ... 64022 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.22.5-1_i386.deb) ...
dpkg: error processing fglrx-control_8.22.5-1_i386.deb (--install):
 trying to overwrite `/usr/share/applnk/fireglcontrol.kdelnk', which is also in package fglrx-6-8-0
Errors were encountered while processing:
 fglrx-control_8.22.5-1_i386.deb
me@MELINUX-UBUNTU:~/Desktop/Downloads$ sudo dpkg -i xorg-driver-fglrx_8.22.5-1_i386.deb
(Reading database ... 64022 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.22.5-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx_8.22.5-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx_8.22.5-1_i386.deb
```

What is wrong?

---

### Post by superm1 on 2006-02-27
It appears you have a very old fglrx driver installed as well.  Remove that, and then retry the steps you were at.

---

### Post by ins on 2006-03-06
Dont know if you've fixed it yet; but try this:
```

sudo apt-get remove fglrx-6-8-0

```
Then proceed with the intall

---

### Post by cotcot on 2006-03-06
I have used this with success : [http://www.student.dtu.dk/~s971652/ati_radeon.shtml](http://www.student.dtu.dk/~s971652/ati_radeon.shtml)
I hope this will help you.

---

