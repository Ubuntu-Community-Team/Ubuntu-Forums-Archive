---
title: "dependencies used by each application"
date: 2012-01-27
forum: General Help
---

### Post by elliotn on 2012-01-27
is the a way I can get a list of dependency used by each application, eg FireFox, vlc, gstreamer etc 

what I want to do is have a list of packages used by each application. any idea

---

### Post by satanselbow on 2012-01-27
Simples ;) ... when you know it... impossible if you don't...

```
apt-cache depends <package>
```

To do it in reverse ie what packages depend on it

```
apt-cache rdepends <package>
```

---

### Post by cortman on 2012-01-27
```
dpkg-deb -I foo.deb
```

Gives info on the package, including dependent packages...

Satanselbow's method works if the package is installed.

---

### Post by Frogs Hair on 2012-01-27
The synaptic package manager can  be used  also if installed . Right click the line that displays the package and enter properties > dependencies .

---

### Post by elliotn on 2012-01-27
thanks guys I will mark it solved

---

### Post by satanselbow on 2012-01-27
> **cortman said:**
> 
Satanselbow's method works if the package is installed.


Not quite correct. It works for anything found in your currently enabled repos - installed or not ;)

However I hadn't considered downloaded debs ;)

---

### Post by cortman on 2012-01-27
> **satanselbow said:**
> Not quite correct. It works for anything found in your currently enabled repos - installed or not ;)

However I hadn't considered downloaded debs ;)

You're right. I had tested it out on a deb not gotten from the repos. Thanks!

---

