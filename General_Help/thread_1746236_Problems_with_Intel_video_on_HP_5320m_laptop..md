---
title: "Problems with Intel video on HP 5320m laptop."
date: 2011-05-01
forum: General Help
---

### Post by zonky on 2011-05-01
Hi, I have some fairly weird problems with my HP 5320m laptop. Has on-board Intel graphics on Natty.

When the computer boots, monitors shows that I have 2 screens present, but mirrored - however only the laptop screen is present.

[http://img690.imageshack.us/img690/310/monitoratbootup.jpg](http://img690.imageshack.us/img690/310/monitoratbootup.jpg)

It gets weird when i add my external monitor via the HP displayport:

[http://img683.imageshack.us/img683/7617/monitorchangedposition.jpg](http://img683.imageshack.us/img683/7617/monitorchangedposition.jpg)

As you can see- somehow my laptop screen is being duplicated, and i can't change the position of my external monitor.

Really not sure where to start on this. Work absolutely fine in 10.10.

---

### Post by zonky on 2011-05-01
Not sure how to determine exactly what driver in use, but:

```
:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

---

### Post by zonky on 2011-05-03
There is a bug assigned, seems to affect this notebook model:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773734](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773734)

---

