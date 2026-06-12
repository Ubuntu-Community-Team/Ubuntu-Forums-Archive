---
title: "Do I have a firewall?"
date: 2011-03-23
forum: General Help
---

### Post by sofasurfer on 2011-03-23
I never installed one, but if I wanted to find out for sure if I have one how would I do that?

---

### Post by lisati on 2011-03-23
The firewall which comes as standard with Ubunut is [iptables]("https://help.ubuntu.com/community/IptablesHowTo"). You might also want to take a look at [ufw]("https://help.ubuntu.com/community/UFW").

As well as this, many modern routers come with firewall facilities.

---

### Post by madmax75 on 2011-03-23
> **sofasurfer said:**
> I never installed one, but if I wanted to find out for sure if I have one how would I do that?

AFAIK, Ubuntu comes with a built-in firewall utility (iptables). Ufw is the command-line utility to manage iptables (I hope this is even a remotely correct description :D).

You might want to install the **gufw **graphical front-end for ufw from the Synaptic package manager or from the Software Center. After installation, navigate to Gufw from your menus (it should be under System -> Administration -> Firewall Settings - the little white-blue shield icon), and click it on. That's it.

---

