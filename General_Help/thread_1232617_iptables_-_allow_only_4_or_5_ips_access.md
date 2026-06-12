---
title: "iptables - allow only 4 or 5 ips access"
date: 2009-08-05
forum: General Help
---

### Post by abazoskib on 2009-08-05
I want to block all traffic on port 80 accept when coming from about 4 or 5 IP addresses. how do i set that up? iptable config is not my strong suit, and i would appreciate any help i can get because this is a very sensitive issue

---

### Post by abazoskib on 2009-08-07
any ideas?

---

### Post by Brandon Williams on 2009-08-08
I use iptables directly, but there are also wrappers that can simplify the use of iptables. I don't use such wrappers, so I'll just tell you how I would do this with iptables.

To drop incoming packets destined for tcp port 80:
```
sudo iptables -I INPUT --proto tcp --dport 80 -j DROP
```

To accept such packets from a specific source (for example, 10.10.10.10):
```
sudo iptables -I INPUT --source 10.10.10.10 --proto tcp --dport 80 -j ACCEPT
```

The -I flag (insert) creates the new rule as the first one in the chain. It's important to add the drop rule before the accept rules, since the accept rules need to come before the drop rule in the chain.

After you've got the rules set up so that they work correctly, you then want to make sure that they get added whenever you reboot. To do this, I first run:
```
sudo iptables-save | sudo tee /etc/default/iptables
```

And then I add the following line to /etc/rc.local, above the exit:
```
iptable-restore </etc/default/iptables
```

If you ever add new rules by hand, just run the iptables-save command line again.

---

