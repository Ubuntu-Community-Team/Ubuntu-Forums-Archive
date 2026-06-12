---
title: "LAMP Stack and BIND"
date: 2011-05-17
forum: General Help
---

### Post by monkeytooth on 2011-05-17
Sooo I am entirely new to the whole Linux experience. I know from reading Ubuntu is likely one of the few flavors I actually want to use...

I wanna set up a standard LAMP stack, I also want to set it up as a production server (well in sorts) I need it to act as a remote development environment but the best way to think of it is production as it will be open to the world in a matter of speaking. My ISP allows the connections, the ports aren't blocked. However the IP changes frequently, I don't know how and when or why (if its triggered).. But I do know that that does hinder the set up of the stack a bit, as I want to have a domain pointing to the server (or more than one I may set up a couple virtual hosts for various projects I have going on). So.. I guess my ultimate question here is, how do I go about setting this all up (I know its not all some super easy task, and I know I may be new to linux and setting stuff up on it, but I am not new to Computers in general, or working with servers, so that said any help is appreciated even if its "advanced")

---

### Post by falko on 2011-05-17
Regarding the LAMP stack, take a look here: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp)

Regarding the DNS stuff, I suggest you get a hostname from dyndns.org and configure your router to update that hostname record whenever your IP changes. You can then set up CNAME records for your domains that point to your dyndns.org hostname.

---

### Post by Lars Noodén on 2011-05-17
> **monkeytooth said:**
> ...However the IP changes frequently, I don't know how and when or why (if its triggered)...

Try using a [Dynamic DNS](https://help.ubuntu.com/community/DynamicDNS) service.

---

