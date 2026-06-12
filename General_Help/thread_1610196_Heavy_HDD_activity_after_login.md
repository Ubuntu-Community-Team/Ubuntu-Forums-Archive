---
title: "Heavy HDD activity after login"
date: 2010-10-31
forum: General Help
---

### Post by undisclosedname on 2010-10-31
I'm running Ubuntu 10.10 on an Acer Aspire 5530G.

On a fresh install, the HDD is silent after logging in and the desktop is immediately ready for use. 

A few days and updates later, after every login, there's heavy HDD activity that lasts about 20/30 seconds and makes it almost impossible to perform any other task. The entire desktop is visible during said event.

Not a big issue, however it bothers me a little. I've observed this behavior since Ubuntu 9.10. Anyone else experiencing similar problem? Any solution?

Thanks!

---

### Post by J V on 2010-10-31
I've never heard of this problem, had you set it to start up a program on login? I have tons of programs start automatically but I only ever get about 10 seconds max lag after login...

Could you check the logs?

---

### Post by TeoBigusGeekus on 2010-10-31
Run top (or even better htop) during that heavy activity period to see what's eating up cpu and memory.

---

### Post by undisclosedname on 2010-10-31
Hello guys, thanks for your help. I installed htop and ran it after logging it and noticed that the ubuntuone process was using more system resources than usual. I disabled it under System > Preferences > Startup Applications and the problem is gone.

It's strange because I've been using Ubuntu One since I've installed Ubuntu 10.10 on 10/10/10 and only today the heavy activity problem has started to occur.

J V How do I check the logs?

---

### Post by J V on 2010-10-31
system admin logviewer, but they are hard to read and you won't need it now ;p

---

