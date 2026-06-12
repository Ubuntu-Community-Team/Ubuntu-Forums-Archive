---
title: "VNC Problems with Ubuntu 10.04"
date: 2010-08-26
forum: General Help
---

### Post by xhaggotx on 2010-08-26
I am trying to view my Ubuntu Desktop from a Windows 7 machine
I have my VNC viewer installed on the windows machine and remote desktop enabled on Ubuntu
When I connect to my Ubuntu desktop I can see the Gnome desktop but I cannot see my interactions with it, but I can see the interactions on the monitor attached to the ubuntu machine
eg: I can use the vnc desktop to click on a window as to move it and move it and I can see it moving on the monitor connected to the ubuntu machine but I cannot see it moving on the VNC window on the windows machine
What is wrong? I can post details of config files if needed, i just need to know which ones

---

### Post by beowulf1416 on 2010-09-27
you probably have compiz enabled. there is an issue with vnc and compiz right now.

---

### Post by anglican on 2010-09-28
> **xhaggotx said:**
> I am trying to view my Ubuntu Desktop from a Windows 7 machine
I have my VNC viewer installed on the windows machine and remote desktop enabled on Ubuntu
When I connect to my Ubuntu desktop I can see the Gnome desktop but I cannot see my interactions with it, but I can see the interactions on the monitor attached to the ubuntu machine
eg: I can use the vnc desktop to click on a window as to move it and move it and I can see it moving on the monitor connected to the ubuntu machine but I cannot see it moving on the VNC window on the windows machine
What is wrong? I can post details of config files if needed, i just need to know which onesAre you sure that you're looking at the same desktop? Remote desktop starts up a new desktop normally i.e. it doesn't show :0 but :1. To see :0 you need x11vnc.

H

---

### Post by HermanAB on 2010-09-28
Please note that VNC presents a serious security problem and your machine is at risk of getting hacked if you leave the server running.  Consider installing Cygwin on Windows and ssh-server on Linux instead - then from a Windows cygwin terminal you can do:

ssh -C -c blowfish -X user@linuxipaddress gnome-panel

and go click happy on the Gnome taskbar and run any Linux application transparently on the Windows desktop.

---

### Post by linux-hack on 2010-09-28
You can take a look at this : [http://www.linux-hack.org/tutos/linux-tutos/fun-xnest-howto/](http://www.linux-hack.org/tutos/linux-tutos/fun-xnest-howto/)

and you can channel the informations stream trough a ssh connection.

---

