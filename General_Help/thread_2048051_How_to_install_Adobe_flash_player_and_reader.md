---
title: "How to install Adobe flash player and reader?"
date: 2012-08-26
forum: General Help
---

### Post by grcee on 2012-08-26
Please help me!
When I was trying to install adobe plash player and reader , I found following Error. Help me to get install them.

grc@grc-G31M:~$ sudo apt-get install flashplugin-installer acroread/
[sudo] password for grc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package acroread
grc@grc-G31M:~$ 

Thanks

---

### Post by gandaran on 2012-08-26
you need to enable the partner canonical repository in software sources first and update package list then acroread will be available for install.
ubuntu  software center » edit » repositories » other software tab

---

