---
title: "Internet Wont Connect, WTF?!? Help Needed ASAP!"
date: 2009-09-19
forum: General Help
---

### Post by secuono on 2009-09-19
I've had ubuntu for 2yrs, upgrade to the newest verisons whenever they come out. Sometimes the internet wont connect and i have to restart my PC a few times for it to work again. But it will not connect anymore. Why? I have the latest version of ubuntu, up to about 3 months ago. How do I connect to the internet again???

---

### Post by solidblu on 2009-09-19
Wireless?

Wired?

do you get an ip address? (ifconfig)

---

### Post by secuono on 2009-09-19
I tried this-
sudo apt-get --purge remove pppoeconf
-and then rebotted and it worked! I dodn't know if that was even related, found it at-
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/70588](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/70588)

Thanks so much for trying to help anyway!
:P

hopefully it continues to work...^.^

---

