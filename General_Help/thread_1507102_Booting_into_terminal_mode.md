---
title: "Booting into terminal mode"
date: 2010-06-11
forum: General Help
---

### Post by jabe_z on 2010-06-11
Hi all,

I'm using a system with nvidia graphics card gt220 with driver version 190. I tried installing mplayer and that installation procedure upgraded my nvidia driver. The installation was not successful and it gave an error that there are some broken packages. I ignored that warning and shutdown the system. When i tried to boot again after some time, it took me to a terminal instead of login screen.

I tried to recover the system using "report broken packages" option from recovery mode. I could able to delete all the broken packages. After removing all the broken packages, i tried to install nvidia drivers using command "apt-get install nvidia-glx-190". 

I'm getting this following error and the situation remains same. 

```
preparing to replace nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa4 (using .../nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa14_i386.deb) ... dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
Unpacking replacement nvidia-glx-190 ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa14_i386.deb(--unpack): trying to overwrite '/usr/lib/libvdpau_nvidia.so', which is also in package nvidia-190-libvdpau 0:190.42-0ubuntu~karmic~nvidiavdpauppa4
processing triggers for man-db
processing triggers for desktop-file-utils ....
processing triggers for libc-bin ....
ldconfig deferred processing now taking place
Errors were encountered while processing:
/var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

please help me. I am unable to get into the desktop. Only thing i'm seeing now is a flickering screen with terminal. 

Jabez.

---

### Post by jabe_z on 2010-06-11
Do i have to format my system?? is that the only solution for the above problem? :( :( :(

---

### Post by Peter09 on 2010-06-11
boot into recovery (command prompt) mode and do the following commands.
 
```
sudo apt-get update
```
 
and 
 
```
sudo apt-get upgrade
```

---

