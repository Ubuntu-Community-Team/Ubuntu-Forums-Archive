---
title: "'Write failed: broken pipe&quot; for stale SSH sessions"
date: 2010-07-09
forum: General Help
---

### Post by GammaPoint on 2010-07-09
Hi all, I'm using the newest version of Ubuntu and I have problems with SSH sessions being disconnected after a couple minutes of inactivity with the error "Write failed: broken pipe". My SSH setup before the upgrade didn't result in these problems.

Any ideas what I might be able to do to keep the session from disconnecting? I saw this problem a couple times on these forums but didn't see an explicit solution for it.

---

### Post by k.mooijman on 2010-07-10
Same here 
but if an application is running it maintains the link open and functional
looks a bit like an safeguard but still annoying.

---

### Post by GammaPoint on 2010-07-10
> **k.mooijman said:**
> Same here 
but if an application is running it maintains the link open and functional
looks a bit like an safeguard but still annoying.

Bah, yeah. This is strange and annoying problem. Maybe if I just run 'more' or something on a file at the end of when I'm using it then it'll stay active, but that's annoying to have to do.

---

### Post by archenroot on 2011-10-07
Hey, I am facing the same issue when connection from my notebook to server located in DMZ. I tried to add:
SSH client config file> /etc/ssh/ssh_config 
line> ServerAliveInterval 60
SSH daemon config file> /etc/ssh/sshd_config
line> ClientAliveInterval 60

Hope it will solve my problem as soon as I am not connected over  internet, so I think this is not related to some broken communication on  way of signal, but will see...

If you are connecting over internet or VPN, this could be done by automatic restarting of VPN service, router failures, etc...much harder to explore the root cause of issue with disconnecting.

Ladislav

---

