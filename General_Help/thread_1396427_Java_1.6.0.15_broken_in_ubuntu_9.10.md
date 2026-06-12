---
title: "Java 1.6.0.15 broken in ubuntu 9.10"
date: 2010-02-02
forum: General Help
---

### Post by etano on 2010-02-02
I'm having some fairly severe java issues. I typically use chromium browser.  One day, presumably after an update, java stopped working in chromium with the following error:

```
The following plug-in has crashed: /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnpjp.so
```

I also have firefox and epiphany installed, java fails for them as well.  

about:plugins shows the java 1.6.0.15 plugin as installed.  I have tried reinstalling java a couple times now with various iterations and sun-java and open-jdk/iced tea. Nothing seems to work.  Please help!

---

### Post by moted on 2010-02-02
I'm using the Chromium dailies with JRE 1.6.0.18 and I've also seen this issue over the last few days.

Perhaps rolling back to the Chromium Beta is a better solution.

---

### Post by etano on 2010-02-02
Has this worked for you?  Also, I don't see why the chromium installation version should affect other browsers capacity to run java as well.

---

### Post by scouser73 on 2010-02-02
For installing the latest 32 & 64 bit version of Java please follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Although on the site it states that it's only for Ubuntu 9.10, I have installed it on Ubuntu 9.04 and it works flawlessly.

---

### Post by moted on 2010-02-02
If it was working previously to an Chromium update, it's unlikely that updating the JRE will affect anything.  I'm currently running the latest JRE and the latest daily builds of Chromium crashed with the java plugin.

I reverted to the Beta PPA and rolled back Chromium and the issue has been resolved.

---

### Post by etano on 2010-02-03
Switched to chromium beta ppa, rolled back chromium, everything is working.  Odd, but I'll take it!

---

### Post by roshats on 2010-02-11
i had this problem in Firefox (namoroka) 3.6.2pre and Google chromium. i  followed this steps: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)  . now it's ok in namoroka but not in chromium

---

