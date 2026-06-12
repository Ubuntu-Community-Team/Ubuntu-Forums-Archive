---
title: "su: Authentication failure"
date: 2009-08-28
forum: General Help
---

### Post by h3lLx0x on 2009-08-28
I currently want to install Java.

when i type su it goes Authentication failure
 why??

---

### Post by nothingspecial on 2009-08-28
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by t0p on 2009-08-28
You're problem is that you're using the **su** command.  This requires you to type in the root password.  But a default installation of ubuntu does not have a root password set.  What you need to do is prefix your commands with **sudo**, and follow them with your user password when prompted.

---

