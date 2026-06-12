---
title: "Remote Desktop ?"
date: 2006-05-08
forum: General Help
---

### Post by GekkeHenk on 2006-05-08
I'm using Ubuntu 5.10 and have configured remote desktop to work. It works in my own network but now I'm at school and I can't login. Which port does the remote desktop use and how can I set it up correctly.

---

### Post by the_tiger on 2006-05-08
It depends how you have set up your remote desktop. If you are logging in over the internet you should really use ssh to ensure that your connection is encrypted and your password may not be seen when you login.

I used the VNC over SSH wiki to set up a secure tunnel and then followed the resumable sessions post to login to GDM. VNC is a program for viewing remote screens. SSH creates an encrypted connection so that your session will be secure.

VNC over ssh.
[https://wiki.ubuntu.com/VNCOverSSH?highlight=%28vnc%29](https://wiki.ubuntu.com/VNCOverSSH?highlight=%28vnc%29)

This method will give you an X-terminal (windows and a terminal screen.)

In order to have resumable sessions try this. Some users have suggested it is less secure but as I long as you set up an ssh connection first I believe it is ok. (Enabling any form of remote access will always make a machine less secure.)

[http://ubuntuforums.org/showthread.p...hlight=gdm+vnc](http://ubuntuforums.org/showthread.p...hlight=gdm+vnc)
[I]edit:[http://www.ubuntuforums.org/showthread.php?t=122402&highlight=gdm+vnc]("http://www.ubuntuforums.org/showthread.php?t=122402&highlight=gdm+vnc")
[/I]
In order for remote access to work from across the internet you will need to ensure that your home firewall/router will forward the ports used by ssh and vnc. These are mentioned in the posts and I believe they are 22 for SSH and 5900/5901 for VNC.

---

### Post by GekkeHenk on 2006-05-08
I want to use the remote desktop connection using the software from windows XP, it works on the network. I forwarded the port 5900 & 5901. I don't have access to my Ubuntu PC atm because I'm at school.

---

### Post by the_tiger on 2006-05-08
I assume you are using the ISP assigned to you by your sevice provider, not your local network IP? Also are the ports forwarded directly to the machine you are trying to access and have you also forwarded the required packets? If you are using windows software it is still highly recommended to set up an ssh connection or your passwords will be transmitted unencrypted over the internet for all to see.

---

### Post by stanz on 2006-05-08
[quote=the_tiger]
[http://ubuntuforums.org/showthread.p...hlight=gdm+vnc]("http://ubuntuforums.org/showthread.p...hlight=gdm+vnc")[/quote] 
**Not Found**

 The requested URL /showthread.p...hlight=gdm+vnc was not found on this server.



ooops....

---

### Post by the_tiger on 2006-05-08
Link repaired

---

### Post by stanz on 2006-05-27
Thanks tiger....I'm soon gonna need this help- later on!!

---

