---
title: "Internet/Network Manager problems"
date: 2010-12-12
forum: General Help
---

### Post by Big Smooth on 2010-12-12
My brothers computer uses Ubuntu. All of a sudden the internet stopped working. So I did some research online and found a site that looked like it would work because the comments were good. I did what it said by removing the network manager and then i had to re-install it blah blah blah. Long story short his computer is still without internet. I tried to download the network manager on my computer and install it on his computer. I dont think it worked.

If anyone could help me find the correct network manager to download for his computer and then help me get internet back onto his computer I would appreciate the help.

Hes using Ubuntu 9.10. 

Thanks, 

Ryan

---

### Post by Krytarik on 2010-12-12
[http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=network-manager&searchon=names&suite=karmic&section=all)

How did you remove the network-manager, do you know exactly which packages has been removed? Those have have to be reinstalled then.

EDIT: If removed with the "apt-get"-command via terminal, look in /var/log/apt for the history; if removed with Synaptic, go to "File -> History".

---

### Post by Big Smooth on 2010-12-12
This was the coding I was trying to use. Im not sure what all was removed. Is there a way I can find that out?

sudo apt-get remove network-manager-gnome network-manager

ifconfig

gksu gedit /etc/network/interfaces

auto
iface lo inet loopback

auto eth0
iface eth0 inet static
address *insert ip address here*
netmask 255.255.255.0
gateway 192.168.0.1

gksu gedit /etc/resolv.conf

nameserver 208.67.222.222
nameserver 208.67.220.220

sudo /etc/init.d/networking restart

---

### Post by Big Smooth on 2010-12-12
In the history there waas term.log and then term.log.1.gz term.log.2.gz  term.log.3.gz term.log.4.gz term.log.5.gz term.log.6.gz

---

### Post by drdos2006 on 2010-12-12
If this is 9.10 desktop then I would reinstall network manager with :
sudo apt-get remove network-manager-gnome network-manager

Then I would cahange the static IP address to automatic DHCP with :

sudo gedit /etc/network/interfaces

Type :
auto lo
iface lo inet loopback

and restart the network
sudo /etc/init.d/networking restart 
 I would then check to see if I had an IP address with 
ifconfig

and then if still no joy, I would consider IPv6 problems.
Please post back

regards

---

### Post by Krytarik on 2010-12-12
> **Big Smooth said:**
> In the history there waas term.log and then term.log.1.gz term.log.2.gz  term.log.3.gz term.log.4.gz term.log.5.gz term.log.6.gz
No history.log, history.log.1.gz or such? Anyway, just download the packages you included in the remove-command and try to install them, first network-manager, then network-manager-gnome: right-click at them in the file-browser and choose "Open" or "Open with... Gdebi". There might be further dependencies, if so, Gdebi will give a warning with the missing file-name. Post them here, or search for them on your own via the search tool of the site I posted.

On the other hand, how should the internet connection be established, theoretically?

---

### Post by Big Smooth on 2010-12-12
I installed both. They worked fine. Didnt come up with any warnings or missing files. The internet runs from a router upstairs and is wired to his computer downstairs.

---

### Post by Big Smooth on 2010-12-12
double post sorry. I just tried going to a website and it works fine. Thanks for the help.

---

