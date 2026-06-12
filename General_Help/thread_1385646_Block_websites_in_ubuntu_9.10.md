---
title: "Block websites in ubuntu 9.10"
date: 2010-01-19
forum: General Help
---

### Post by Dinesh Balaji on 2010-01-19
hi guys!! i need a way to block websites in Ubuntu!! im using UT starcom Modem!! Plz help me!! thnx;)

---

### Post by john newbuntu on 2010-01-19
Option1: turn off your modem 
Option2: install gufw or firestarter and configure it.

---

### Post by mikewhatever on 2010-01-19
It's actually very simple. Add a line to /etc/hosts that look like the following:

```
127.0.0.1   websiteURL
for example
127.0.0.1   ubuntuforums.org
```

---

### Post by n0dix on 2010-01-19
Use iptables. It's a tricky to configure but it's very powerfull.

---

