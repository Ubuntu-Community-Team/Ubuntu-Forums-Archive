---
title: "moblock won't start :("
date: 2011-02-09
forum: General Help
---

### Post by anti-other on 2011-02-09
Hey, what's up ^_^
I'm pretty new to Ubuntu. I installed the moblock, mobloquer, and blockcontrol thing cuz I use Peer Guardian 2 on my Windows partition. When I start MoBlock it updates all my lists and then when it's done updating it throws this error:

iptables v1.3.3: invalid port/service 'SSL'specified
Try'iptables -h' or 'iptables --help' for more information.
...fail!
Operation started: 9/2/2011 - 18:02:29
Inserting iptables ...
iptables: Chain alredy exists.
...fail!
[see attached screenshot]

I haven't got the slightest what's wrong, I only installed Ubuntu a short while ago, so I'm **NEW** to it. **How should I fix this!!** Thank you for the help!!

---

### Post by dino99 on 2011-02-09
i've not tried it recently but always have failed , so i prefer iplist as i can authorized "on the fly" for a special need and let reject otherwise

add this ppa to synaptic repo tab (third parties)

[https://launchpad.net/~ssakar/+archive/ppa](https://launchpad.net/~ssakar/+archive/ppa)

then update, install it

---

### Post by anti-other on 2011-02-09
**Bahahaaaa**.. Got it working!! I think it's cuz I had IMAP and SSL whitelisted in the blockcontrol configuration at: dpkg-reconfigure blockcontrol.
I ran **dpkg-reconfigure blockcontrol**, re-did it, but took **whitelisting** for **IMAP** and **SSL** **off**, reloaded and restarted, and **BLAM!!** Working ^_^

---

