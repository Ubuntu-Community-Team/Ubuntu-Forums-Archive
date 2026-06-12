---
title: "Determine how many times your Ubuntu system has rebooted?"
date: 2011-10-04
forum: General Help
---

### Post by gatorguy on 2011-10-04
I'm trying to find a log or file that will help me determine how many times a system has rebooted. I know on a Windows system you can parse through the system event log and there are certain event ID's that only happen at boot up. I'm fairly new to Ubuntu and trying to find something that would provide that type information.

Thanks in advance for any feedback,
Gatorguy

---

### Post by Toz on 2011-10-04
From a terminal window, try:
```
for file in `ls /var/log/wtmp*`; do last -f $file | grep reboot; done
```

For more info: [http://manpages.ubuntu.com/manpages/hardy/man1/last.1.html]("http://manpages.ubuntu.com/manpages/hardy/man1/last.1.html")

---

### Post by gatorguy on 2011-10-04
Thanks for the quick reply! I'll give that a shot.

Gatorguy

---

### Post by tgalati4 on 2011-10-04
Yikes!  I was having some problems with some thinkpad hotkeys:

tgalati4@tpad-Gloria7 ~ $ for file in `ls /var/log/wtmp*`; do last -f $file | grep reboot; done
reboot   system boot  2.6.28.10-slim   Mon Oct  3 20:00 - 18:08  (22:08)    
reboot   system boot  2.6.28.10-slim   Sun Oct  2 13:15 - 18:08 (2+04:52)   
reboot   system boot  2.6.28.10-slim   Tue Sep 27 07:42 - 18:08 (7+10:26)   
reboot   system boot  2.6.28.10-slim   Tue Sep 20 22:40 - 18:08 (13+19:28)  
reboot   system boot  2.6.28.10-slim   Sun Sep 18 20:25 - 18:08 (15+21:43)  
reboot   system boot  2.6.28.10-slim   Sun Sep 18 16:47 - 20:24  (03:37)    
reboot   system boot  2.6.28.10-slim   Sun Sep 18 13:34 - 16:45  (03:11)    
reboot   system boot  2.6.28.10-slim   Tue Sep 13 14:31 - 12:47 (4+22:15)   
reboot   system boot  2.6.28.10-slim   Tue Sep 13 12:46 - 14:26  (01:40)    
reboot   system boot  2.6.28.10-slim   Tue Sep 13 11:53 - 12:44  (00:51)    
reboot   system boot  2.6.28.10-slim   Tue Sep 13 11:16 - 11:51  (00:34)    
reboot   system boot  2.6.28.10-slim   Tue Sep 13 10:52 - 11:15  (00:23)    
reboot   system boot  2.6.28.10-slim   Tue Sep 13 09:54 - 10:50  (00:56)    
reboot   system boot  2.6.28.10-slim   Tue Sep 13 08:47 - 09:43  (00:55)    
reboot   system boot  2.6.28-19-generi Tue Sep 13 07:05 - 08:46  (01:41)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 22:56 - 07:04  (08:07)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 22:29 - 22:55  (00:25)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 21:55 - 22:27  (00:31)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 21:08 - 21:54  (00:46)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 20:41 - 21:03  (00:21)    
reboot   system boot  2.6.28.10-some-s Mon Sep 12 20:08 - 20:33  (00:25)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 19:48 - 20:07  (00:19)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 19:04 - 19:47  (00:42)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 15:54 - 19:03  (03:08)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 14:56 - 15:51  (00:54)    
reboot   system boot  2.6.28.10-slim   Mon Sep 12 09:44 - 13:11  (03:26)    
reboot   system boot  2.6.28.10-slim   Sun Sep 11 19:14 - 09:43  (14:29)    
reboot   system boot  2.6.28.10-slim   Sun Sep 11 18:02 - 19:13  (01:11)    
reboot   system boot  2.6.28.10-slim   Sun Sep 11 17:43 - 18:00  (00:17)    
reboot   system boot  2.6.28.10-slim   Sun Sep 11 17:10 - 17:41  (00:31)

---

