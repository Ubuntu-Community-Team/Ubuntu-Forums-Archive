---
title: "Install Sun's JAVA"
date: 2006-02-07
forum: General Help
---

### Post by iemand on 2006-02-07
Hi everybody, 

Can anyone help me in installing Sun's JDK ? 
I downloaded the latest (JDK 1.5.0.6) JDK I installed it, but now I want to make Sun's jdk default Java. (I downloaded the binary self extractor format, changed its permission with chmod and then started it)

When I make a sudo update-alternatives --config java I don't see the JDK I installed. 

So I wonder, 

Is it possible 
- to remove these 2 VM I see when I execute the command sudo update-alternatives --config java
- to use Java's Sun implementation instead of I don't know which version of Java is used by default with KUbuntu. 

In advance thanks to all :)

---

### Post by Vinger on 2006-02-07
Automatix can install that (and other programs) for you...

grz

---

### Post by Perfect Storm on 2006-02-07
Or

```
sudo gedit /etc/apt/sources.list
```

add:
 

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install sun-j2re1.5

```

---

### Post by iemand on 2006-02-07
Hi, 
I've already installed it in /usr/local/. 
I want it there and nowhere else. Can I still use it ? or I have to uninstall it and réinstall it using apt-get ? :-( 

Thanks

---

