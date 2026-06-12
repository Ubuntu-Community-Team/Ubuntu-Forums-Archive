---
title: "Sun Java not working after clean install 10.04"
date: 2011-06-27
forum: General Help
---

### Post by mystmaiden on 2011-06-27
I just did a clean install of Ubuntu 10.04 and now I can not get Sun Java working. Java is enabled in the browser and below is what --version shows. 
```
java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)

```I tried installing icedtea, but it was no help so I have it and open jdk currently removed from the computer. I'd love some help with this, we use Java a lot.

thanks,

mystmaiden

---

### Post by spcwingo on 2011-06-27
Did you have all the Sun-Java stuff installed?  If not, run this in a terminal:

```
sudo apt-get install -y sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

EDIT:  Oh, if any of the OpenJDK stuff is installed, remove it first.

---

### Post by bab1 on 2011-06-27
> **mystmaiden said:**
> I just did a clean install of Ubuntu 10.04 and now I can not get Sun Java working. Java is enabled in the browser and below is what --version shows. 
```
java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)

```I tried installing icedtea, but it was no help so I have it and open jdk currently removed from the computer. I'd love some help with this, we use Java a lot.

thanks,

mystmaiden

You need to configure it.  See [URL="https://help.ubuntu.com/community/Java"][B]_this page_.
[/B][/URL]

The section is "Choosing the default Java to use"

The actual command is ```
sudo update-alternatives --config java
```

---

### Post by mystmaiden on 2011-06-28
Thanks so much for the replies. I tried to configure it but it gave me 'nothing to configure' so it must have been a package I was missing. Its working now though.

---

