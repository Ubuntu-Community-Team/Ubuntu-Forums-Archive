---
title: "Upgrading Ubuntu Version without losing data.."
date: 2010-03-20
forum: General Help
---

### Post by karthick87 on 2010-03-20
Currently i am using Ubuntu 9.04(Jaunty),i have downloaded iso image of Ubuntu 9.10 and i have burned it in a CD..So how to upgrade my ubuntu version to 9.10 without losing existing data..Thanks in advance..!

---

### Post by darolu on 2010-03-20
To upgrade from 9.04 to 9.10 you are going to need the Alternate CD, not the LiveCD. Network upgrade is recommended though, follow the instructions in this link: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by karthick87 on 2010-03-20
I have got 9.10 live cd,using that is it possible to upgrade?If not is there anyway to upgrade my ubuntu version without network connection..

---

### Post by linden940 on 2010-03-20
why dont you want to do it by the network?

---

### Post by karthick87 on 2010-03-20
Upgrading the version using network takes lot of time,so i would like to use cd..

---

### Post by linden940 on 2010-03-20
hmmm ok...i dont see how it takes alot of time.

---

### Post by wojox on 2010-03-20
Put the cd in and try:

```
sudo apt-cdrom add
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by darolu on 2010-03-20
> **getyourkarthick said:**
> I have got 9.10 live cd,using that is it possible to upgrade?If not is there anyway to upgrade my ubuntu version without network connection..

Unoftunatelly you need the alternate CD, not the LiveCD; I am not sure if the method wojox suggest works, it would most like upgrade via network with "apt-get dist-upgrade". If the machine has access to the Internet, -even with the Alternate CD- you will be downloading a lot of packages, depending of how many non-default programs you have installed plus all the updates that have came out over the last (almost) 5 months.

---

