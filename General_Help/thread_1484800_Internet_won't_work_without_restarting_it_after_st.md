---
title: "Internet won't work without restarting it after startup"
date: 2010-05-16
forum: General Help
---

### Post by inha on 2010-05-16
After upgrading to 10.04 I've had to run /etc/init.d networking restart to get my internet connection to work after startup on my desktop computer. Any ideas on how to find out what's wrong and how to fix it? I didn't uprage my laptop yet and it still works just fine so I'm thinking this is related to the upgrade. Softwarewise the only relevant networking related difference between my desktop and laptop is the ubuntu version and that I have openvpn set up on the desktop for work related stuff. 

Any ideas would be appreciated!

---

### Post by dcstar on 2010-05-16
> **inha said:**
> After upgrading to 10.04 I've had to run /etc/init.d networking restart to get my internet connection to work after startup on my desktop computer. Any ideas on how to find out what's wrong and how to fix it? I didn't uprage my laptop yet and it still works just fine so I'm thinking this is related to the upgrade. Softwarewise the only relevant networking related difference between my desktop and laptop is the ubuntu version and that I have openvpn set up on the desktop for work related stuff. 

Any ideas would be appreciated!

If you upgraded from something that is not Upstart compatible then possibly it is running before the network comes up.

Remove any strange software and see if the networking works without it.

---

### Post by inha on 2010-05-16
> **dcstar said:**
> If you upgraded from something that is not Upstart compatible then possibly it is running before the network comes up.

Remove any strange software and see if the networking works without it.

I removed openvpn and resolvconf and now it works straight away, thanks! Now I'll just have to figure out how to set them back up without causing this problem again.. #-o

Edit: I'm thinking that resolvconf caused this, since openvpn isn't started automatically.

---

