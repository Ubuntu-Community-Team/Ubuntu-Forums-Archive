---
title: "Problems getting to ubuntu.com/using software center from home connection"
date: 2012-08-26
forum: General Help
---

### Post by Siekacz on 2012-08-26
I have serious problems with ubuntuforums.org, ubuntu.com (and subdomains)m launchpad.net and canonical.com. I can't see any website, download software from USC, check for updates and install them. Nothing works. This happens only when I'm using my home internet conenction. On 3G everything works fine.
Traceroute: [http://screencloud.net/v/ysK4](http://screencloud.net/v/ysK4)

---

### Post by CharlesA on 2012-08-26
Moved to it's own thread.

Please check your DNS settings in /etc/resolv.conf or try a different DNS server such as 8.8.8.8.

If you are able to tracert or ping ubuntu.com, it isn't a DNS issue and you should look elsewhere.

In the screenshot, it looks like you did a traceroute to *ubutnu.com* not ubuntu.com

---

