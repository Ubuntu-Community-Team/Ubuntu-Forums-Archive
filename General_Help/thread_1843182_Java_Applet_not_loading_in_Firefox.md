---
title: "Java Applet not loading in Firefox"
date: 2011-09-13
forum: General Help
---

### Post by satish_j on 2011-09-13
Iam using Openjdk on Lucid.For enabling Java applets,i installed IceadTea plugin from synaptic,restarted the browser,but the applets still refuse to load.
Any ideas how to solve it?

---

### Post by vasa1 on 2011-09-13
Satish, which browser are you using? I understand that Opera doesn't play well with IcedTea.
Also, if possible, could you list a couple of links that don't display the applets?

---

### Post by psrdotcom on 2011-09-13
might be JRE location issue.

---

### Post by gandaran on 2011-09-13
> **satish_j said:**
> Iam using Openjdk on Lucid.For enabling Java applets,i installed IceadTea plugin from synaptic,restarted the browser,but the applets still refuse to load.
Any ideas how to solve it?
remove icedtea and install sun-java6-plugin

---

### Post by satish_j on 2011-09-13
> **vasa1 said:**
> Satish, which browser are you using? I understand that Opera doesn't play well with IcedTea.

Its Firefox..
specified in Thread title...

---

### Post by satish_j on 2011-09-13
pls do not suggest to go for sun java,i have been using openjdk w/o any issues for last 2yrs..i think this is not related to Openjdk plugin..

---

### Post by linux2001 on 2011-09-13
look here
[http://plugindoc.mozdev.org/linux.html#Java]("http://plugindoc.mozdev.org/linux.html#Java")

---

### Post by gandaran on 2011-09-13
> **satish_j said:**
> pls do not suggest to go for sun java,i have been using openjdk w/o any issues for last 2yrs..i think this is not related to Openjdk plugin..
okay, but just to let you know openjdk doesn't work on some websites, only sun-java can.

---

### Post by satish_j on 2011-09-14
well,this is what helped
```

ln -s /usr/lib/jvm/openjdk6/jre/plugins/i386/IcedTeaPlugin.so /usr/lib/firefox-3.6.13/plugins

```

---

