---
title: "Ubuntu Server could not connect to update"
date: 2011-04-23
forum: General Help
---

### Post by GK320 on 2011-04-23
Hi all. I just got a server box with Ubuntu 9.04 installed from my work place.

It just got the command line and I wish to install the GUI, Since I'm very new to ubuntu..

I have my server connect to my home router and all the port forwarding is done. I could see the webpage on the server. 

When I use sudo apt-get update

It shows&#65306; 0% [Connecting to 10.135.0.3(10.135.0.3)][Connecting to 10.135.0.3(10.135.0.......
and then it tells me unable to connect to 10.135.0.3 8080:

When I test the connect with host google.com, I got reply (Which means my server has the access to the internet?)


Also I tried cat /etc/network/interfaces  
It shows me(Comments are not included):

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp





--Im just fishing around the internet and actuall i have no idea what im doing now....

---

### Post by bmathis on 2011-04-23
Check your sources and see if there is any non-Ubuntu repositories in there 
> sudo nano /etc/apt/sources.list
if there is, comment it out with a # at the begging of the line. Then try updating again.

---

### Post by GK320 on 2011-04-23
Thanks for the reply, the url all looks good and related with ubuntu site...

---

### Post by GK320 on 2011-04-23
If no one can think anyother problem, I think I might just try to reinstall the Ubuntu server............

---

