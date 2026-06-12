---
title: "Firewall for Jaunty"
date: 2010-04-04
forum: General Help
---

### Post by sp3kter on 2010-04-04
Hello Everyone,

I'm a first time Linux user.Just installed version 9.04 along with Ubuntu Restricted Extras,Torrent clients and Empathy messenger (amongst other things.)
[I mention the above few because I suppose they require incoming connections?]

I'd be grateful if anyone could recommend a very easy to use GUI based Firewall and antivirus (if needed.)

I'm not behind a router,just using an ADSL modem to connect.

Thank you.

---

### Post by sxmaxchine on 2010-04-04
you dont realy need an anti virus but you can try avast you will need to type that into google.

---

### Post by Enigmapond on 2010-04-04
Ubuntu comes with it's own firewall..iptables. In the terminal type:

```
sudo ufw enable
```This will enable the firewall and tell it to start each time you boot. By default, it's configured to deny all incoming connections unless it's in response to your outgoing request. An easy way to set rules and such is simply to install gufw.

Unless you are running a server, or have a windoze partition, you will not need an anti-virus as viruses and malware are virtually non-existent with Linux.

---

### Post by sp3kter on 2010-05-07
Sorry for the late reply.
Got it working.
Thanks a tonne.:)

---

