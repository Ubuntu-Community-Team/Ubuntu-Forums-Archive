---
title: "Getting a domain name"
date: 2010-07-25
forum: General Help
---

### Post by goodvikings on 2010-07-25
Hey guys
 
Some quick questoins about hosting a website. I have a bit of experience with linux, but nothing really to do with web hosting as yet.
 
I have a server running ubuntu 8.04 with apache2. What I'd like to know is how to go about setting up a domain name? I've looked at a heap of hosting sites, but they son't seem to allow you to specify your own IP address that you already have.
 
Also, I'm not sure about what, if any kind of DNS software I would then have to run on my server.
 
At this stage I'm only doing preliminary research about it I guess. Still, any help would be appreciated.

---

### Post by lmarmisa on 2010-07-25
Maybe you can use some dynamic DNS service:

[http://www.dyndns.com](http://www.dyndns.com)

[http://www.no-ip.com]("http://www.no-ip.com/index.php")

Kind regards,

Luis

---

### Post by lisati on 2010-07-25
> **lmarmisa said:**
> Maybe you can use some dynamic DNS service:

[http://www.dyndns.com](http://www.dyndns.com)

[http://www.no-ip.com]("http://www.no-ip.com/index.php")

Kind regards,

Luis

+1 to the suggestions. I have domain names with both services. It's sometimes slightly easier to use with a static public IP address (which, depending on your ISP, will *can* attract an extra charge on your monthly bill): just tell your choice of host what your IP address is, and forget about it until they (no-ip, dyndns or whoever) send you a reminder to keep their records up to date. If, however, like many people, you have a dynamic public IP address that is likely to change from time to time, both services have remote clients available that run on your server to do this for you. If you're lucky, your router and/or modem will have an option to let you do the update automatically (mine does, but sadly only one at a time).

---

