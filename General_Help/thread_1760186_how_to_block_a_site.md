---
title: "how to block a site?"
date: 2011-05-16
forum: General Help
---

### Post by ahsan08 on 2011-05-16
Can anyone please help me : how to block a website in ubuntu 11.04, so that, none can visit the site from my pc???

---

### Post by doas777 on 2011-05-16
in your /etc/hosts file, add a line like:
```
127.0.0.1     <siteurl>
```that way, whenever your PC ask for the address of that site, it comes back localhost.

if that is not flexible enough for you, look into the OpenDNS service. you can use it to block addresses as well.

---

