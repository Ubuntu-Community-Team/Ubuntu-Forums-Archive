---
title: "School Network"
date: 2010-04-19
forum: General Help
---

### Post by ride4mud on 2010-04-19
Hello.  I currently administer a small private school network which contains 45 Windows XP computers.  The IT budget for the school has evaporated due to state funding being pulled.  I am planning on converting the network as follows:

(1) Server:  Windows 2003 to be converted to Ubuntu Server 10.04
(2) Lab (30 desktops):  Windows XP to be converted to Ubuntu Desktop 10.04
(3) Teachers / Admin (15 desktops):  Windows XP to remain Windows XP.

I am looking for some tips and traps from people that have attempted this.  I have also begun to test this type of network at my home using some of the school's older hardware.  I have made great progress with Ubuntu Desktop running on an old Dell and it out performs XP hands down.

The server is up and running with Samba but one of the problems I have not been able to solve is how to setup the Ubuntu desktop to function as a workstation to the server.  At the desktop login screen I want to be able to log into the computer using an account on the server (similar to a Windows workstation).  Can anyone tell me or point me in the correct direction for this?  Thank you.

---

### Post by lisati on 2010-04-19
I haven't actually used it myself, but think that [LTSP]("https://help.ubuntu.com/community/UbuntuLTSP") might be one option to consider.

---

### Post by Iowan on 2010-04-19
I was gonna suggest [LDAP]("https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html"), but LTSP might be more what you had in mind...

---

