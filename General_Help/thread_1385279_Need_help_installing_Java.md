---
title: "Need help installing Java"
date: 2010-01-19
forum: General Help
---

### Post by realoperadeal on 2010-01-19
Any help on this would be great. I need Java to look at a webcam on my work website. 
Thanks!

---

### Post by Techsnap on 2010-01-19
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

When it's done restart your browser.

---

### Post by realoperadeal on 2010-01-19
Thanks for that - it says it is configuring java and has the installation licence on the screen. It won't let me click ok - does that mean it's still working? it's been about 15 minutes now.

---

### Post by arubislander on 2010-01-19
press on tab until the OK 'button' is highlighted, then press enter.

---

### Post by Uncle Spellbinder on 2010-01-19
Mine installed rather quickly. I used the following command...

```
sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin unixodbc
```

---

### Post by realoperadeal on 2010-01-19
working perfectly now, thanks!

---

### Post by scouser73 on 2010-01-19
For installing the 32 & 64 bit version of Java please follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Although on the site it states that it's only for Ubuntu 9.10, I have installed it on Ubuntu 9.04 and it works flawlessly.

---

