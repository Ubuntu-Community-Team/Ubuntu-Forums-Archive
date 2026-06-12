---
title: "SSH X forwarding help"
date: 2009-07-25
forum: General Help
---

### Post by nahira on 2009-07-25
I'm new to linux so please bear with me!
 I have an ubuntu LTS server on my desktop. On my laptop I have windows and I have  putty and Xming installed. I can connect to the server and type “gedit” and see the graphical display. Now I installed ubuntu LTS on my labtop and I do ssh -X -p xxx user@server_ip but when I type “gedit” the graphical doesn't display, I don't get any error message either. So I thought it might be the ubuntu on my laptop so I did ssh to the school server and type “gedit” and it displays the GUI.
 On my server I check /etc/ssh/sshd_config  and
 X11Forwarding yes 
 X11DisplayOffset 10 
 I also have xauth install on the server. "apt-get install xauth"

 I also read the old thread on the forum [http://ubuntuforums.org/showthread.php?t=22558](http://ubuntuforums.org/showthread.php?t=22558)
 I thought it is ssh and X forwarding problem.

Can anyone please tell me what am I missing?
 Thanks

---

### Post by nahira on 2009-08-03
Oh I finally figure out what is going on. It is some firewall on the switch that is causing the problem. I don't get the UI when I'm on the local network but it works fine when I'm connection from an outside network.

---

