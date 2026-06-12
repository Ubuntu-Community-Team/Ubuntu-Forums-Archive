---
title: "remove vindaloo pdf viewer"
date: 2009-09-12
forum: General Help
---

### Post by s.mcclatchie on 2009-09-12
Hello -- Does anyone out there know how to get rid of the vindaloo pdf viewer that seems to be associated with google desktop and with catfish? 

It doesn't seem to disappear with 
 sudo dpkg -r google-desktop-linux

nor can I remove it in the usual ways:

smc@nakrasana:~$ sudo dpkg -r vindaloo
dpkg - warning: ignoring request to remove vindaloo which isn't installed.

smc@nakrasana:~$ sudo apt-get remove  vindaloo --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vindaloo

I suspect that the viewer is part of both google desktop and catfish since it does not appear to be a stand-alone application:

smc@nakrasana:~$ vindaloo
bash: vindaloo: command not found
smc@nakrasana:~$ 

This viewer gets in the way of using evince or something equally sophisticated.

Any ideas on how to disable it?

Thanks -- Sam

---

