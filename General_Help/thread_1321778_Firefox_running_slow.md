---
title: "Firefox running slow"
date: 2009-11-10
forum: General Help
---

### Post by Kirk202 on 2009-11-10
Upgraded to Ubuntu 9.10 and it also upgraded Firefox to 3.5 from 3.0 and now it runs very slow.  I've been using Epiphany but some of the websites I use require Firefox.  Everything else operates just fine.

Any recommendations?

Thanks.

---

### Post by hwttdz on 2009-11-10
Run firefox at the command line and see if there are any errors/warnings.

---

### Post by Digikid on 2009-11-10
disable ivp6 from within Firefox.

---

### Post by hwttdz on 2009-11-10
To do that type about:config in the address bar, then ipv6 in the find box, then doubleclick ipv6 and change true to false or the other way around.

---

### Post by ZiJuan on 2009-11-10
Sorry, I don't use Ubuntu 9.10, still Ubuntu 9.04. But I think the firefox of Ubuntu 9.04 is much better. Why change it? Hope you can resolve it soon. Good Luck!):P

---

### Post by wojox on 2009-11-10
Try some of these tweaks [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Kirk202 on 2009-11-10
Thanks everyone,

I disabled ipv6 but didn't seem to help and went to wojox's link and changed the config as per recommendations - seemed to help a little.

Thanks again for the help.

---

### Post by hwttdz on 2009-11-10
This is sometimes caused by the dns servers, try using a different dns server, such as those provided by opendns.  Make sure to save your original ones, I find it's often best to just copy your current connection settings then change the dns servers.  Let me know if you have any questions about setting up a new connection.

208.67.222.222
208.67.220.220

I didn't like the opendns not found page so I added an entry in my hosts file for that page, and rerouted it to google.

---

