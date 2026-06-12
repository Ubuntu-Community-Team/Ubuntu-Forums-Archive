---
title: "Login screen does not load"
date: 2009-06-29
forum: General Help
---

### Post by pjaikins on 2009-06-29
I have Ubuntu 8.10 which has until now been working fine. Today, I had changed the login screen theme and had installed the TimeVault application. I then logged out of my session and the screen went to the default Ubuntu sand background and the spinning disk, but the login prompt never loads. I have rebooted multiple times and can login as root and user from the command prompt. 

Can someone please help me to find out how I can recover?

---

### Post by upbeat.linux on 2009-07-01
Have you tried booting into recovery mode and troubleshooting from there?

---

### Post by jarrah-95 on 2009-09-01
try using 
```
 
sudo apt-get purge TimeVault

```
(btw if your using root then cut the sudo off)

---

