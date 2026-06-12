---
title: "Local Web-Server"
date: 2010-09-09
forum: General Help
---

### Post by Crizzie on 2010-09-09
Hi,

Does anyone know of a good tutorial to setup a **secure** local web-server on my computer? I just want a local web-server so I'm able to install php/mysql and create some websites/php applications I've been wanting to do now for awhile.

I just want something that's secure and not going to let any outsiders on my computer. I'm still very new to Ubuntu so I don't have the slightest idea of security.

---

### Post by bodhi.zazen on 2010-09-10
First if you are behind a router that helps 99.99 % of the security issues.

You can also configure Apache to listen only on 127.0.0.1. 

You can configure iptables to drop all connections outside of 127.0.0.1 or you LAN.

You can also look at :

[HOWTO: Setup easy web development environment (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")

---

### Post by Crizzie on 2010-09-10
I was considering using XAMPP, simply for the fact that everything I would really need is right there in that package. Is there still a way to configure Apache to only listen on 127.0.0.1 with XAMPP? I'm just really nervous about security.. I don't want to open my system up.

---

### Post by Crizzie on 2010-09-10
I just read somewhere that it's possible for someone to hack your XAMPP install directory and gain access to your system. I just don't know what to do anymore.. :cry:

---

### Post by bodhi.zazen on 2010-09-10
> **Crizzie said:**
> I just read somewhere that it's possible for someone to hack your XAMPP install directory and gain access to your system. I just don't know what to do anymore.. :cry:

Restrict access with your router and configure xampp or apache to listen only on 127.0.0.1

---

### Post by Nythain on 2010-09-10
im with bodhi here... people cant access what they cant access, if there's no door in, and no one is there to answer the door, then chances are, somones not getting in (ok, bad analogy because burglars can break in and all that jazz)

If you dont port forward or open up the ports on your router, your router will block connections on port 80 to begin with...

If someone does make it through your router, a proper iptables entry will drop all incomming connections from anything other than your local machine (127.0.0.1)

If apache isnt listening on any adress other than localhost, then its not really a security vulnerability anyways, because as hard as someone may try, there's just nothing on port 80 to sneak in through that they can access...

of all of that, the router should be default and a simple telling apache to only listen on localhost (again 127.0.0.1) should be more than enough to run a secure web server on your system no accessible by anyone not sitting at your computer

---

