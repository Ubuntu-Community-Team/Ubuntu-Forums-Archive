---
title: "fail to connect internet in ubuntu 11.10"
date: 2011-10-24
forum: General Help
---

### Post by Debarghya on 2011-10-24
sir, i have newly installed ubuntu 11.10 but i failed to connect broadband connection. i have siemens modem. i configured through sudo pppoe.but when try to connect internet it fails. plog gives-
Oct 24 12:17:20 ubuntu pppd[2178]: Using interface ppp0
Oct 24 12:17:20 ubuntu pppd[2178]: Connect: ppp0 <--> eth0
Oct 24 12:17:21 ubuntu pppd[2178]: CHAP authentication failed: CHAP authentication failure, unit 3203
Oct 24 12:17:21 ubuntu pppd[2178]: CHAP authentication failed
Oct 24 12:17:21 ubuntu pppd[2178]: Connection terminated.

please tell me what should i do?

---

### Post by Debarghya on 2011-10-24
pls tell me,i cann't do anything.

---

### Post by niindb on 2011-10-24
I have recently installed Ubuntu 10.11, and am unable to connect LAN broadband and wireless broadband. I've tried Ubuntu help, but it's not working, probably because the nomenclatures used in the help section and the nomenclatures that I actually find in 10.11 version are different, and therefore difficult to understand for a beginner like myself. Please help.

---

### Post by dineshs on 2011-10-25
If your modem is in bridge mode try
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
If you have any difficulty please post the output of the following terminal command```
sudo lshw -C network
```

---

