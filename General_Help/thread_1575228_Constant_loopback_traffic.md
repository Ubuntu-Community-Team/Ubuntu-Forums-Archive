---
title: "Constant loopback traffic"
date: 2010-09-15
forum: General Help
---

### Post by Maintech on 2010-09-15
I have a question about why the loopback traffic is so heavy. When I run Conky I show connections from localhost (loopback 127.0.0.1) connecting back to itself by tcp but it shows it is an "outbound" connection. When viewing from wireshark it shows 127.0.0.1 (loopback) connecting to 127.0.0.1 using tcp. It is almost a constant connection to a variety of ports. They include 57224, 37686, 57225, 52967, 37686. That is just a small sample of the ports. I can not find a common usage for them in ICAN ports lists. I have 2 computers that have Ubuntu 10.04 on them and both are doing this so I have to assume this is how the operating system now works. None of my previous Ubuntu have done this. I would like to know what exactly is happening and why. Also, some of my loopback communications are using IPV6 which I have never observed any of my computers doing before.

---

### Post by Maintech on 2010-09-15
Bump

---

### Post by Maintech on 2010-09-15
Bump
I really need to know if this is normal Ubuntu behavior.

---

