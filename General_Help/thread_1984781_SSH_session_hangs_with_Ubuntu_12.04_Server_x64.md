---
title: "SSH session hangs with Ubuntu 12.04 Server x64"
date: 2012-05-22
forum: General Help
---

### Post by eyatsko on 2012-05-22
Hello!

I have strange problem. SSH hangs after several minutes of inactivity. I checked all SSH settings, but I did not find something pointing on a problem cause... I even don't know what to post here... :-(

May you help me. It bothers very much - to enter username/password and to do "su -"  tens times per day..

P.s. My computer is under Windows XP SP3 has no similar problems with Ubuntu 10.04 Server x64.

Kind regards,
Ellad Yatsko

---

### Post by eyatsko on 2012-05-22
I forgot to mean that I tried to set up SSH-session to "problem Ubuntu" from ANOTHER UBUNTU (mentioned above 10.04 Server). And it remained connected!

---

### Post by Nicholas Lee on 2012-05-22
If you are using PuTTY, you might want to start with looking under the 'Connection' settings for the parameter 'Settings between keepalives (0 to turn off).
 
The default is '0', but if you change this to '120' seconds then it will prevent the connection from dying.
 
I found this worked for me, going from XP and Windows 7 PCs to Ubuntu 12.04 LTS.

---

