---
title: "Does iptables need to reboot to delete rules?"
date: 2010-03-21
forum: General Help
---

### Post by TheAlien on 2010-03-21
When you set rules in iptables by using the terminal, like blocking outgoing traffic, I really can't reset iptables back its default state by writing **$ sudo iptables -F** to flush all rules. If I block all outgoing traffic, the outgoing traffic is still blocked after the Flush command has been used. To be able to get outgoing traffic again, I'll need to restart the whole machine and OS.

Are there any commands that can reset iptables without rebooting, so I can block and unblock outgoing network traffic without rebooting?

---

### Post by huygens on 2010-03-21
This is weird. Iptables does not need reboot, as soon as you change it, it is "activated".
I guess there is something else that does a side effect.

How exactly do you proceed to block all outgoing traffic (command lines, software?)?
How do you check that this is blocked?
How do you check that this is no longer blocked after flushing iptables?

If you answer those questions, I might be able to help you further on.

---

### Post by gmargo on 2010-03-21
You can delete individual firewall rules rather than flushing the tables completely. But rather than running **iptables** yourself, you should try using a firewall package, like the default **ufw** firewall.  Let it handle the nit-picky details.

---

