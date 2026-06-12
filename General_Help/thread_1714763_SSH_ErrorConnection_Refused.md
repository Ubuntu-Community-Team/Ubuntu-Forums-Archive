---
title: "SSH Error:Connection Refused"
date: 2011-03-25
forum: General Help
---

### Post by dhollingsworth on 2011-03-25
Hi,

I've just completed a fresh install of Ubuntu Server (x64) on a HP Proliant N36L.  During the installation I selected to install LAMP, SAMBA and SSH.  To continue the installation of software on the server I wanted to connect remotely from windows PC on the same LAN.  I am using PuTTY but when I try to connect I get "Error: Connection Refused".  I have trawled the forums regarding the setup of putty and openssh and everything appears to be correctly configured.

I have checked that the services are running on the server and that the IP address for the server is correct.

The guides I have read online suggest that ssh should be correctly configured as part of the install, so why can I not connect from the same LAN?

Is the firewall enabled by default during install?

Advice to overcome this would be much appreciated.  I am a little peeved that this doesn't work out-of-the-box.

Thx

Dave

---

### Post by JaizEdelmann on 2011-03-25
did you try and chk status of UNF?

> sudo ufw disable

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by dhollingsworth on 2011-03-25
Ah ah!  Yes you were right!

"sudo ufw allow 22"  sorted it.

Thanks for the heads up.


Dave

---

