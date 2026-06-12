---
title: "Remote Desktop Help"
date: 2009-08-31
forum: General Help
---

### Post by mcgooie on 2009-08-31
I hope someone out there can help me. what i am looking to do is setup my ubuntu desktop so that i can access it from outside my home network via a windows xp machine.

i have tried various guides and the most success i have had is with this one - [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) - i can connect using the address 192.168.x.x but when i use my network ip with ports forwarded i get connect to host xxx.xx.xx.xx port 22: connection refused error message.

can anyone point me in the way of an easy to follow step-by-step guide so i can get this working?

thanks

---

### Post by okmat on 2009-08-31
are you shure you're using your public ip? 

do you have a static IP internet service? if not you might want to check [http://www.no-ip.com/]("http://www.no-ip.com/")

did you configure the sshd_config file properly (to use port 22 in your case?)

check my guide on freeNX [here]("http://www.redmezzanine.com/?p=160&lang=en")

---

### Post by mcgooie on 2009-09-01
I tried to setup a new fresh install and now i cannot even connect using the network. i get the following error:

NX> 203 NXSSH running with pid: 2728
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.2.2 on port: 5678
Connection closed by 192.168.2.2

any advice?

---

### Post by okmat on 2009-09-04
are you sure you don't have a firewall enabled? try to connect disabling the windows firewall and your antivirus in your windows Box

---

