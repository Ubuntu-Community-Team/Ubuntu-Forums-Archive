---
title: "Ubuntu 11.04 - is there a option to put desktop button to minimize all windows?"
date: 2011-04-28
forum: General Help
---

### Post by kaisar89 on 2011-04-28
Hi all, i just installed Ubuntu 11.04, im still getting use to the interface but im missing one key feature, is there an icon button to go to desktop, to minimise all windows so i can go to desktop?

any help much appreciated. Thanks in advance.

---

### Post by StrayEddy on 2011-04-28
I believe you can still use the shortcut:
 
super + d - OR 
control + alt + d
 
Don't know for the button though, sorry...

---

### Post by kaisar89 on 2011-04-28
windows + D works, just found that out, ideally should have and icon that you could click on.

---

### Post by THE CARTER on 2011-04-28
Actually, there is a way.  


Run the following commands in a terminal:

sudo apt-get install wmctrl
cd
wget [http://webupd8.googlecode.com/files/showdesktop.tar.gz](http://webupd8.googlecode.com/files/showdesktop.tar.gz)
tar -xvf showdesktop.tar.gz && rm showdesktop.tar.gz
sudo mv showdesktop /usr/local/bin/

Then navigate to your home folder and drag and drop the showdesktop.desktop file on your Unity launcher.


If that made no sense, follow this link:


[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by kaisar89 on 2011-04-28
> **THE CARTER said:**
> Actually, there is a way.  


Run the following commands in a terminal:

sudo apt-get install wmctrl
cd
wget [http://webupd8.googlecode.com/files/showdesktop.tar.gz](http://webupd8.googlecode.com/files/showdesktop.tar.gz)
tar -xvf showdesktop.tar.gz && rm showdesktop.tar.gz
sudo mv showdesktop /usr/local/bin/

Then navigate to your home folder and drag and drop the showdesktop.desktop file on your Unity launcher.


If that made no sense, follow this link:


[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)


Hi, i followed your instruction but nothings happen, nor has showdesktop been created in the home folder. 

home@homelinux:~$ sudo apt-get install wmctrl
[sudo] password for home: 
Sorry, try again.
[sudo] password for home: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wmctrl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
home@homelinux:~$

---

