---
title: "Update Manager can't work"
date: 2010-04-30
forum: General Help
---

### Post by wilsondjm on 2010-04-30
After I have installed the 10.04, I found the upgrade manager were not able to connect to the sources. 
It report an error and said:
[http://mirrors.163.com/ubuntu/dists/lucid/Release.gpg](http://mirrors.163.com/ubuntu/dists/lucid/Release.gpg)  can't connect to 127.0.0.1:8080 (127.0.0.1)&#12290; - connect (111: Connection refused)

however, my firefox and other applications are able to get access to the internet. (the network interface eth0 is active and works well). 
Anybody know what the problem is?

---

### Post by mac9416 on 2010-04-30
Howdy, wilsondjm,

The error says "can't connect to 127.0.0.1:8080 (127.0.0.1)&#12290; - connect (111: Connection refused)." I'm not sure why it's even trying to connect to 127.0.0.1 (your own computer). Do you have APT configured to use a proxy?

---

### Post by dino99 on 2010-04-30
anyway there is no more updates to do as you have the latest release.
if you still get same apt or update-manager errors, into a console run:

sudo dpkg-reconfigure apt
or/and 
sudo dpkg-reconfigure update-manager

---

### Post by justinjw on 2010-05-05
My update manager is screwed up after the 10.04 install as well.  When I run it from the menu, nothing happens.  I tried running it from the terminal, I got the following error:

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 30, in <module>
    import gconf
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/gconf.so: cannot read file data: Input/output error


Any suggestions?

---

### Post by justinjw on 2010-05-09
Any ideas?  It seems like my gconf.so file is corrupt.  Can someone post the contents of this file, or send me a copy to replace it?

Thanks!

---

