---
title: "remote desktop"
date: 2010-09-16
forum: General Help
---

### Post by tdm333 on 2010-09-16
hello dose anyone know how i can get remote desktop to work on a outside Internet connection i can get it to work on my router but my brother cant access it from his pc i have vnc view on his pc but ever time i try to connect from his pc it keep saying cant connect any idea how i would fix this i have the firewall on my lunix system turned off

---

### Post by supershin on 2010-09-16
What about his router? Sounds like the you can connect to him from your pc but he can't connect to you from his, is that it? Could be a closed port or his firewall is blocking it. 
A little more detail would help.

---

### Post by tdm333 on 2010-09-17
he dose not have a router he using comcast cable modem how can i poen up ports on ubuntu

---

### Post by wiseseoservice on 2010-09-17
Was thinking that this could be a firewall issue.  Have you checked this?

---

### Post by tdm333 on 2010-09-17
lol if i knew why this would be easer to do but i dont do remote desktop to offten i used msn for it but cant run msn messenger on lunix

---

### Post by supershin on 2010-09-18
I assume you're using ubuntu but is he? Is he using winXP/Vista/7? 
What vnc software are you both using? How do you connect to the net, through a router or direct through modem? 

How about you give details on the setup you both have? Unless you do this, its unlikely more people will respond.

---

### Post by bodhi.zazen on 2010-09-18
First, VNC is insecure, use FreeNX or tunnel it over ssh.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

If you wish to connect over the internet, you will need to configure your router to forward port(s).This varies by router.

[http://portforward.com/](http://portforward.com/)

Be sure you understand the security implications, VNC is the most common crack on these forums.

---

### Post by tdm333 on 2010-09-25
well he is run windows xp but i turn his firewall off and mine but i still cant connect to my pc from his would it be the port forwarding that is messing me up from connecting to my system btw im runing ubuntu at the hose and im trying to connect to it with windows xp home sp 2

---

### Post by bodhi.zazen on 2010-09-25
> **tdm333 said:**
> well he is run windows xp but i turn his firewall off and mine but i still cant connect to my pc from his would it be the port forwarding that is messing me up from connecting to my system btw im runing ubuntu at the hose and im trying to connect to it with windows xp home sp 2

If the PC you are trying to connect to is behind a router, yes you need to forward the port.

Please note the security implications of doing so, VNC is one of the most commonly cracked servers.

---

### Post by junapp on 2010-09-25
maybe take a look at teamviewer.
[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

---

### Post by jjakspaw6 on 2010-09-25
Teamviewer is a good choice for remote connections. I personally use Logmein. ([http://logmein.com](http://logmein.com))
you shouldn't have any trouble with firewall settings using these...

---

