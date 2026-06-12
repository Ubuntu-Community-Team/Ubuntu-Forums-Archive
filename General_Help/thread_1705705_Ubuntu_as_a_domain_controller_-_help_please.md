---
title: "Ubuntu as a domain controller - help please"
date: 2011-03-12
forum: General Help
---

### Post by markeee on 2011-03-12
Hi,

Could someone point me in the right direction for setting up a ubuntu machine as a domain controller

Basically
1x Ubuntu box,

6 clients all running Windows (XP/7)

I want to have the user authentication system controlled by the Ubuntu box, as well as roaming profiles, so when I login to windows it loads /home/user as the My Documents folder on the Windows machine

I've come across various guides but I'm still not 100% about what I need to do !!

Do I need to use OpenLDAP?

Thanks!!

---

### Post by AdRock952 on 2011-03-12
I'm in the process of doing the same with 10.10.  Let me know how you gt on

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by Iowan on 2011-03-12
The [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") might help - this one is for 10.04.
I think [this]("https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html") is buried in there, somewhere.

---

### Post by markeee on 2011-03-12
> **AdRock952 said:**
> I'm in the process of doing the same with 10.10.  Let me know how you gt on

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

thanks!

are you going to be using OpenLDAP??

---

### Post by markeee on 2011-03-12
> **Iowan said:**
> The [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") might help - this one is for 10.04.

thanks mate will try and have a go :)

---

### Post by deconstrained on 2011-03-12
Install dnsmasq and configure /etc/dnsmasq.conf if you also want to use it as a gateway.

---

