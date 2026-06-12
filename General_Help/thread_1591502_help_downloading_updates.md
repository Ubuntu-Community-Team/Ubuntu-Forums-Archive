---
title: "help downloading updates"
date: 2010-10-09
forum: General Help
---

### Post by zelguedez on 2010-10-09
hi, i installed ubuntu 10.04 yesterday and have some problems, every time i tryed to update o download from the system (like the file to reproduce mp3 or to get an aplication from the download center) it said that it fail to download the information to the repositorium

there is something i am missing? thanks for your time

---

### Post by roccivic on 2010-10-09
No internet? Proxy? What is the output if you open a terminal and type in:

```
sudo apt-get update
```

---

### Post by zelguedez on 2010-10-09
internet yes, proxy :confused: mmmm as far as i know is direct from internet (better let me check)

---

### Post by zelguedez on 2010-10-09
done, i change the proxy (it was fixed manualy) and can download aplications, but cant get the mp3 codec to rythmbox

---

### Post by t4thfavor on 2010-10-09
Sounds like a different problem for a different thread, try searching for the lame codec, I believe thats the one that does all mp3 related stuff.

---

### Post by sikander3786 on 2010-10-09
> **t4thfavor said:**
> Sounds like a different problem for a different thread, try searching for the lame codec, I believe thats the one that does all mp3 related stuff.
Don't exactly remember if it is the lame codec. But,

```
sudo apt-get install ubuntu-restricted-extras
```

will do the job. It even will install other video/audio codecs, java, flash, fonts etc. At least, saves me a lot of my time.

---

### Post by efflandt on 2010-10-09
If you need to use a web proxy, just setting that in your browser may not help for other applications (like getting packages or updates).

Set the proxy in System > Preferences > Network Proxy if you have not done that.  That should work for all applications.

---

### Post by mjsh401 on 2010-10-10
Hello Every one
I installed ubuntu 10.04 on a computer in my university. I want to connect to internet. when I do that in win xp I use proxy 192.168.4.10:8080. also for connecting I enter an authentication username and password. But when I enter these setting in Synaptic Package Manager from Setting>Preference>Network it cannot connect to internet. It is intresting for me beacause I can connect to internet by firefox.
plz help me freinds.

---

### Post by sikander3786 on 2010-10-10
> **mjsh401 said:**
> Hello Every one
I installed ubuntu 10.04 on a computer in my university. I want to connect to internet. when I do that in win xp I use proxy 192.168.4.10:8080. also for connecting I enter an authentication username and password. But when I enter these setting in Synaptic Package Manager from Setting>Preference>Network it cannot connect to internet. It is interesting for me because I can connect to internet by firefox.
plz help me friends.
You can try to setup system vide proxy in System > Preferences > Network Proxy as mentioned in **efflandt's** post above. All the Gnome Application will follow those settings.

If it doesn't help, it'll be better to start a new thread with some more details, like the error message received in Synaptic etc.

---

### Post by mjsh401 on 2010-10-17
> **sikander3786 said:**
> You can try to setup system vide proxy in System > Preferences > Network Proxy as mentioned in **efflandt's** post above. All the Gnome Application will follow those settings.

If it doesn't help, it'll be better to start a new thread with some more details, like the error message received in Synaptic etc.
I have the same problem again. this is the error!

[SIZE=4][IMG]http://up.iranblog.com/Files73/85d6a09c471948b9944b.jpg[/IMG][/SIZE]

---

