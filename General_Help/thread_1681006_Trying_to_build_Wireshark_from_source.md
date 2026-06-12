---
title: "Trying to build Wireshark from source"
date: 2011-02-03
forum: General Help
---

### Post by Rodayo on 2011-02-03
So I'm trying to follow this guide on how to build wireshark from source. I know I can use apt-get but I want to learn how to build it instead...
[http://www.wireshark.org/docs/wsug_html_chunked/ChBuildInstallBeforeBuild.html](http://www.wireshark.org/docs/wsug_html_chunked/ChBuildInstallBeforeBuild.html)

Anyways, this is getting incredibly frustrating as everytime I try to install something required for wireshark, that thing has it's own required programs. In order to build wireshark I need GTK. When i tried to install GTK, turned out I needed glib and pango. When I tried to install glib, I needed to install zlib. After that glib decided it to tell me to install gettext, rather than telling me earlier. 

So my question is: is there an easy way to do all this?

---

### Post by oldos2er on 2011-02-03
Try ```
sudo apt-get build-dep wireshark
```

---

### Post by Rodayo on 2011-02-03
> **oldos2er said:**
> Try ```
sudo apt-get build-dep wireshark
```
Damn, had I known such a command existed it would've been the first thing I tried. >_<

Fortunately, all that work paid off and I built all the dependencies and wireshark is up and running. I will definitely try that out in the future though. Thank you

---

### Post by oldos2er on 2011-02-03
You're welcome.

---

