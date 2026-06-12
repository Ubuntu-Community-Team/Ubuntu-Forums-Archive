---
title: "java on windows and ubuntu"
date: 2009-10-01
forum: General Help
---

### Post by tarunck on 2009-10-01
hi,

I developed a full screen (alwaysOnTop) java swing application on windows and it used to run fine. Now i changed my OS to Ubuntu but the application is getting stuck i donno why..
I know that Java is platform independent but is there any dependence?

---

### Post by DrScum on 2009-10-01
You do have the same JRE's on your Ubuntu and your Win machine?
When you try running the app you do have all necessary permissions set in your Ubuntu environment?
Most certainly do have all customary classes needed by your app available in your Ubuntu environment.

With 3 confident "yes" I wouldn't know why your app hangs.

---

### Post by The Cog on 2009-10-01
It is worth noting that the java that gets installed by default in Ubuntu isn't the Sun one, and you may be seeing compatibility issues. Try this:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
```

---

