---
title: "vncviewer -listen"
date: 2009-12-22
forum: General Help
---

### Post by Cuco3 on 2009-12-22
I'm trying to get reverse VNC working. The problem is, when I use "vncviewer -listen" command then initiate the reverse VNC on the customer's end, it accepts the connection on my end, but nothing shows up on the screen. Here's the output of "vncviewer -listen"

> 
cuco@cucopc:~$ vncviewer -listen
vncviewer -listen: Listening on port 5500
vncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8I'm using a virtualized Win7 machine as the "customer's computer" if that helps. Firewall is turned off on both computers.

---

### Post by Cuco3 on 2009-12-22
Anyone?

---

### Post by pricetech on 2009-12-22
Check your other post on the same subject for my response as well as a few others.

---

### Post by Cuco3 on 2009-12-22
I found an answer.

First, uninstall these programs:

```
sudo apt-get remove tightvncserver
sudo apt-get remove xtightvncviewer
sudo apt-get remove vnc4-common

```Then, run these commands to install an older version of the removed programs.```
wget http://ftp.nl.debian.org/debian/pool/main/v/vnc/vnc-common_3.3.7-14_i386.deb
sudo dpkg -i vnc-common_3.3.7-14_i386.deb

wget http://archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/xtightvncviewer_1.2.9-22_i386.deb
sudo dpkg -i xtightvncviewer_1.2.9-22_i386.deb

```After this, you'll want to configure Synaptic to not upgrade tightvncviewer to the new version that doesn't work with UltraVNC SC. To do this, go to System > Synaptic Package Manager. Once there, type in "tightvnc" and select the tightvncviewer program. Then go to Package > Lock Version. After that, you'll have to run the following command to "ensure that synaptic and apt-get respect the same locks":
```
 sudo ln -fs /var/lib/synaptic/preferences /etc/apt/preferences
```When you use the "vncviewer -listen" command, use this command instead
```
vncviewer -listen -encodings copyrect
```Source:
[http://ubuntuforums.org/showthread.php?t=1024015](http://ubuntuforums.org/showthread.php?t=1024015)
[http://ubuntuforums.org/showthread.php?t=821902&highlight=disable+updates+specific+packages](http://ubuntuforums.org/showthread.php?t=821902&highlight=disable+updates+specific+packages)
[http://www.averyjparker.com/2005/11/25/running-ultravnc-viewer-under-wine/](http://www.averyjparker.com/2005/11/25/running-ultravnc-viewer-under-wine/)

Thanks for everyone's help.

---

