---
title: "Firewall Question...."
date: 2006-02-22
forum: General Help
---

### Post by jenkins_t on 2006-02-22
Firewall Question....

I have installed Firestarter, which I believe is simply a frontend for "iptables". So on boot, even though firestarter does not run, iptables are still there and "firewalling", right?

---

### Post by frodon on 2006-02-22
Yes, the GUI is usefull only when you want to modify the rules of your firewall, so your firewall is running by default when you boot on ubuntu.
If you want to check that, enter in a terminal : ```
sudo /etc/init.d/firestarter status
```

So yes you're right ;)

---

