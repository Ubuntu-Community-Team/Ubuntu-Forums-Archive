---
title: "Netbeans 11.10"
date: 2011-10-20
forum: General Help
---

### Post by samishal on 2011-10-20
Hello,

I have just done a fresh install of ubuntu 11.10 on my netbook. however when i searched the software center for netbeans. an ide that i use and love i could not find it. going to the netbeans site i found a shell script that enabled me to install it however it seems that it cannot find the java jdk. I have installed java jdk 7 and 6 on my netbook but still i cannot run netbeans.

Please help if you can.

Samishal

---

### Post by oc666 on 2011-11-03
I could not find it either.
But I've try [this guide](http://pasindudps.blogspot.com/2011/10/installing-netbeans-ide-in-ubuntu-1110.html) and it's working.

---

### Post by vat with tux on 2011-11-03
Download netbeans for linux version from below link you will get a .sh file.. now right click that file open it's properties. Now under permission tab make sure that "execution bit" is set. Now just double click it and "run" it. It will start installation wizard...
[http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)

---

### Post by alco75 on 2011-11-03
Yeah, he did that. His issue is he's got no Java runtime.

I'm pretty sure **ubuntu-restricted-extras** installs the OpenJDK, and that works for me on Xubuntu Oneiric, both a fresh install and an upgrade from Ubuntu Natty.

---

### Post by vat with tux on 2011-11-03
I think he said he has installed jdk 6 & 7 .... JDK include JRE ....:)

---

