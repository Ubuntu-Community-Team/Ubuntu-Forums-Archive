---
title: "Why does firefox go to &quot;work ofline&quot; mode automatically?"
date: 2011-11-19
forum: General Help
---

### Post by arroy_0209 on 2011-11-19
I am using ubuntu 10.04 LTS. It often so happens that after starting firefox (3.6.26), if I search for something in google, a comment is shown which says-- firefox is in "work offline" mode and that I should uncheck this and try again. Well, I never select the file->work offline mode in firefox and this takes place automatically. Why? How do I solve this from happening so that firefox remains in "work online" mode always?

---

### Post by LinuxFan999 on 2011-11-19
Open the terminal and type these three commands:


```
sudo apt-get purge firefox
sudo apt-get update
sudo apt-get install firefox 
```

---

### Post by efflandt on 2011-11-19
Is your network up, or slow to connect?  Slow or faulty network may be a reason.

Before that happens in a terminal does:

[LIST]
[*]**ifconfig -a** show a connection with IP address
[*]**route -n** show a proper default route (UG)
[*]**cat /etc/resolv.conf** show proper nameserver(s)
[/LIST]

Although, if your LAN is connected, but internet has a problem, it should not go to offline mode, it would just give an error that it was taking too long (timed out) trying to connect to the website.  At least that is what happened when I recently had some issue with my DSL (which is working now).

---

