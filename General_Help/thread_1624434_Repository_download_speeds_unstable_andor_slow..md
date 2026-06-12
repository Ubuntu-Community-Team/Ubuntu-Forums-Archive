---
title: "Repository download speeds: unstable and/or slow."
date: 2010-11-17
forum: General Help
---

### Post by rocky5051 on 2010-11-17
I installed Ubuntu 10.10 (32-bit) on my PC the other day with WUBI. Everything went well, more or less, and much like my Dell laptop everything seemed to install out of the box. Up to a point anyway.

On the same network as my laptop, both during Ubuntu's installation (when it attempts to download updates/extras) and post-installation in Synaptic and from the terminal (apt), downloads from the repositories are horrendously slow. They will maintain a constant speed of about ~500kb/s for a few seconds, and then eventually the download speed will randomly drop to 3kb/s and persist at this.

Meanwhile, I can watch youtube videos, surf the web, and do anything else I would normally do, and the download speeds obtained for these particular activities remains nominal.

At first I blamed the mirror, and changed it. The same issue occurred even after the change.

My laptop, on the other hand, and on the same network, can obtain speeds far exceeding this and encounters on issues whatsoever. I'm really at a loss.

Additionally, no such network instability is experienced on Windows if I switch to it.

Suggestions, anyone? Thank ya.

(Relevant) PC Hardware Specs:
Ubuntu 10.10 32-bit
PC CHIPS M848A ATX Motherboard
=>SiS900 PCI Fast Ethernet (Onboard)
2 x 1GB Patriot DDR 400 RAM
AMD Sempron 3300 @ 2.2ghz

EDIT: I'd also like to add that I've had previous versions and flavors of Ubuntu on this PC before, however, I've never had the opportunity to test the ethernet card at all up until now.

---

### Post by rocky5051 on 2010-11-18
I experimented with things a little more last night. Apparently the new mirror I picked is fine, but downloading anything from, say, wine's ppa hosted off of launchpad is ridiculously slow if done through apt or synaptic. However, if I download the packages manually via the browser it doesn't seem to be so much of an issue.

Similar weirdness occurs with different download locations. I'd just say its a bad connection if it wasn't so consistent, was a problem with my laptop, and the download speeds themselves didn't always lock themselves down to 3kb/s.

---

### Post by deserthowler on 2010-11-18
For what it is worth, I am having the same kinds of problems and haven't a clue.
Earl

---

### Post by dcstar on 2010-11-18
> **rocky5051 said:**
> I experimented with things a little more last night. Apparently the new mirror I picked is fine, but downloading anything from, say, wine's ppa hosted off of launchpad is ridiculously slow if done through apt or synaptic. However, if I download the packages manually via the browser it doesn't seem to be so much of an issue.

Similar weirdness occurs with different download locations. I'd just say its a bad connection if it wasn't so consistent, was a problem with my laptop, and the download speeds themselves didn't always lock themselves down to 3kb/s.

Experiment with dropping the MTU setting in your Network connection (I use 1454). If large packets are being fragmented poorly then weird things like this can occur.

---

### Post by rocky5051 on 2010-12-10
I realise this is a very belated response, but I hadn't been able to get around with to fixing this up until about now.

I took your advice and dropped the MTU. I ended up having to lower it quite a bit (to 1024 :( ), but it seems to have resolved the issue. I'm updating as we speak, and the download rates are much more acceptable. I mean, it's still possible I've lost some potential with the small fragment size, but I'm not complaining.

For future reference, you can set it temporarily with ifconfig:
```
ifconfig eth0 mtu 1024
```

Or, set it as a static variable in the /etc/network/interfaces file:
```
mtu 1024
```

Thanks for the help. :)

EDIT: I lie, it seems to have lowered the amount of occurrences a bit, but not fully.

---

