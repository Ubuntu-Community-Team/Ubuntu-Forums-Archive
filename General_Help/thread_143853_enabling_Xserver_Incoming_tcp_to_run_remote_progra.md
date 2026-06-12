---
title: "enabling Xserver Incoming tcp to run remote programs"
date: 2006-03-13
forum: General Help
---

### Post by kunji on 2006-03-13
Hi,

I have just about installed Kubuntu on my laptop. I am trying to start an application from a remote machine using ssh. I have tried to use export DISPLAY=mymachine:0 at the remote machine and xhost + in my local machine. It does not work. When I try something like gv at the remote machine, the program eventually quits with a unable to connect to DISPLAY message. 

Other posts in Ubuntu indicate that I need to reset -noincoming tcp option in some gdm.conf file .... How can I  add this Xconfiguration in Kubuntu? If this is not the way ..., how can I set up Kubuntu KDM to allow me receive X connections?  

Thanks!

Kunji

---

### Post by mailcameel on 2006-08-17
Hi,

By editing the /etc/kde3/kdm/kdmrc file;
comment: ServerArgsLocal = -nolisten tcp

and,

edit /etc/X11/xinit/xserverrc file

remove -nolisten tcp

have fun !

---

