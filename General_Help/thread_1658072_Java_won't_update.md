---
title: "Java won't update?"
date: 2011-01-02
forum: General Help
---

### Post by ScytheX10 on 2011-01-02
Hi. Right now I have java -version
```
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) 64-Bit Server VM (build 17.1-b03, mixed mode)

```

I downloaded and ran the bin from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter")
and no errors presented itself, however, when i do java -version the same info as above shows up..
I initially installed java 1.6.0_22 using apt-get, but i installed this via binary file.. do I have to tell my system to use that specific version? 

Also, is there a separate upgrade for a server? ( THe HotSpot server vm) because I run a game for a server, that is java based.


Thanks!
Info:
Ubuntu server 10.04

---

### Post by vangop on 2011-01-02
Update via synaptic or apt-get, don't mess with binaries.
AFAIK when a binary sun jdk is installed, it just unpacks into the current folder, and not installed anywhere.

---

### Post by SnickerSnack on 2011-01-02
> **ScytheX10 said:**
> Hi. Right now I have java -version
```
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) 64-Bit Server VM (build 17.1-b03, mixed mode)

```

I downloaded and ran the bin from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter")
and no errors presented itself, however, when i do java -version the same info as above shows up..
I initially installed java 1.6.0_22 using apt-get, but i installed this via binary file.. do I have to tell my system to use that specific version? 

Also, is there a separate upgrade for a server? ( THe HotSpot server vm) because I run a game for a server, that is java based.


Thanks!
Info:
Ubuntu server 10.04

You probably have to uninstall java through apt, and then reinstall from the binary.  Maintaining binaries can be a hassle, so I'd look for a ppa if I were you.  A Personal Package Archive works much like a repository.

---

### Post by ScytheX10 on 2011-01-02
I wanted to update to _23 for performance reasons.

I fixed it, I just removed the symlink in /etc/laternatives and replaced it with the extracted binary directory. java -version shows _23 and build 19 of HotSpot. 

Solved.
Editing for people in the future
I did this exactly
**cd /etc/alternatives**
**sudo rm java**
**sudo ln -s /newOne/bin/java java**

---

