---
title: "Web Filtering"
date: 2012-03-21
forum: General Help
---

### Post by jeremygotcher on 2012-03-21
I've been in the process of building a house for the last 2 years.. and i'm almost done.. with this complete My kids will all have computers in their rooms with internet access.. one is 12, 10, and 5.. I'm probably going to put Ubuntu on the machines if I can help it.. With this i'm concerned about what they can get access to and would like to know where they go on the web.. is there anything that I can put on either a Ubuntu installation that will allow me to have complete control over their internet access and allow me to monitor their activity?

---

### Post by HiImTye on 2012-03-21
you can use OpenDNS as a content filter
there's also things like gnome-nanny, a quick google search will give you some results
[http://projects.gnome.org/nanny/tour](http://projects.gnome.org/nanny/tour)
[http://lmgtfy.com/?q=ubuntu+11.10+parental+control](http://lmgtfy.com/?q=ubuntu+11.10+parental+control)

---

### Post by jeremygotcher on 2012-03-21
Thanks for the response.. I've used OpenDNS and the past.. the only thing that I didn't like about it that it blocked all the machines on your network not just specific ones.. Do any of these allow you to monitor activity.. I'ts really not that important for it to have that feature but It would be nice..

---

### Post by jeremygotcher on 2012-03-21
Reading.. I think GnomeNanny will do exactly what I need.. thanks..

---

### Post by HiImTye on 2012-03-21
> **jeremygotcher said:**
> Thanks for the response.. I've used OpenDNS and the past.. the only thing that I didn't like about it that it blocked all the machines on your network not just specific ones.. Do any of these allow you to monitor activity.. I'ts really not that important for it to have that feature but It would be nice..
it only blocks all of your machines if you use it as the default DNS on your router *and* you use the default DHCP settings on your computers. you can always specify a different DNS for your connection

---

### Post by sichent on 2012-03-22
Another possibility is to install the web filtering solution on the proxy/router with Ubuntu and let the kids use any os they want. You might need to block direct access to Internet to them using iptables just to force the filtering to be "ON" always.

Once of the latest web filtering solutions that I personally use is qlproxy from quintolabs... I will not post the link here as it may be considered a "promotion" :)

The idea is to have Squid + qlproxy installed on Linux router (x86 or x64 for now.. no ARM or MIPS support is in qlproxy yet) and let them browse the web through it. Of cource your PC may be excluded :)

Best regards
sich

---

