---
title: "Terminal asks for password but locks up"
date: 2011-10-19
forum: General Help
---

### Post by YJSINC on 2011-10-19
Im new to ubuntu and Im trying to fix a problem with my speakers witch requires a command line. I try to plug it in to the terminal window but then asks for my password. I try to type the password but it wont allow me to type.
What am I doing wrong. Here is what I see. Thanks for the help in advance.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

tim@tim-Satellite-L745:~$ echo "options snd-hda-intel model=thinkpad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
[sudo] password for tim:

---

### Post by drs305 on 2011-10-19
When prompted for a password in a terminal, you won't see it as you type. It was considered a security feature. Just type it in, even though you won't see anything. Press ENTER when you have finished.

---

### Post by YJSINC on 2011-10-19
Thanks...  That worked....

---

