---
title: "Help on Xorg installation"
date: 2012-03-01
forum: General Help
---

### Post by sphairos on 2012-03-01
Hi guys,

Need your help cause I m new in Linux world and google couldn't help me.

I try to install x11 server on the following ubuntu version : 
```
ps aux : Linux alfresco 2.6.35-22-server #35-Ubuntu SMP Sat Oct 16 22:02:33 UTC 2010 x86_64 GNU/Linux

cat /etc/issue
Ubuntu 10.10 \n \l
```

so when I try to install it :
```
alien -i x11_64.rpm
```
I get this : 

```
root@alfresco:/# alien -i x11_64.rpm
        dpkg --no-force-overwrite -i xorg-x11-server-xorg_1.11.99.903-2.20120215_amd64.deb
(Reading database ... 53254 files and directories currently installed.)
Preparing to replace xorg-x11-server-xorg 1.11.99.903-2.20120215 (using xorg-x11-server-xorg_1.11.99.903-2.20120215_amd64.deb) ...
Unpacking replacement xorg-x11-server-xorg ...
Setting up xorg-x11-server-xorg (1.11.99.903-2.20120215) ...
Processing triggers for man-db ...

```

Is that mean the installation is done successfully?

when I try to start X server with 'startx' command I get this :
```
/usr/bin/X: error while loading shared libraries: libcrypto.so.10: cannot open shared object file: No such file or directory
xinit:  Server error.

```

What am I missing?

---

### Post by raja.genupula on 2012-03-01
Hi may be this could help you
[https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation](https://help.ubuntu.com/community/ServerGUI#X11_Server_Installation)

---

### Post by sphairos on 2012-03-01
Hello and thanks
Yeah I've seen this link but I get the described errors when doing these commands and I can't get rid of them that's my problem.

---

### Post by raja.genupula on 2012-03-02
please do this 
```
sudo ln -s /lib/libcrypto.so.0.9.8 /lib/libcrypto.so.10
```
and try again . let us know what you got . 
Thank you .

---

