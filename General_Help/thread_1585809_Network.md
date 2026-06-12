---
title: "Network"
date: 2010-10-01
forum: General Help
---

### Post by acontibun on 2010-10-01
Hello, 
 
In Ubuntu when I plug an ethernet cable, what are the commands to check Ip address, renew, release and so on ....
 
I am plugging an ethernet cable but I am not getting any network connection however when I plug the same cable on a windows machine it works fine and gets IP by DHCP.

---

### Post by sikander3786 on 2010-10-01
```

man ifconfig

```

will give you a detailed idea on that.

Post the output of

```

cat /etc/network/interfaces

```

---

### Post by plucky on 2010-10-01
**System > Preferences > Network Connections** and **Add** a wired connection.

It should have enabled it on the  install if you had the wire connected.

Good Luck

---

