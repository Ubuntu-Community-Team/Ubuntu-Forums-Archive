---
title: "How to shutdown firewall permanently?"
date: 2006-06-25
forum: General Help
---

### Post by Ritariassa on 2006-06-25
I have a firewallrouter in my LAN, so I don't need any software firewalls. How can I permanently shut down firewall in Dapper?

---

### Post by adwait on 2006-06-25
As far as I know, there is no firewall enabled by default in Dapper.

---

### Post by asimon on 2006-06-25
The kernel has iptables (Linux' firewall facility) compiled in, but if you don't define any rules, then there in no firewall active. Thus you need not to shutdown anything, but just don't define any rules, which is as adwait sayed the default under Ubuntu.

---

### Post by Thiesen on 2006-06-25
To completly remove all rules set for Netfilter (the framework inside the kernel that handles firewalling/routing/traffic shaping) do this from you favourite terminal:

```

sudo iptables -F
sudo iptables -X

```

That will remove any rules iptables had.

---

