---
title: "Sun Java6 and Package Manager"
date: 2011-08-16
forum: General Help
---

### Post by ajs52698 on 2011-08-16
Hello i have 2 problems.

The first synaptic package manager wont open when i try to open it i get this msg

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Thats my first problem!

My second problem is i cant seem to find sun java6 in in ubuntu software center and i cant find any forums about it.


PLEASE HELP!

---

### Post by merlin371 on 2011-08-16
for the first problem just open a terminal and run "sudo dpkg --configure -a" 

and for the second one, just look for "openjdk" and you should find it

---

### Post by ajs52698 on 2011-08-16
open jdk is sun java?

---

### Post by ajs52698 on 2011-08-16
oh and that didnt fix the package manager problem :(

---

### Post by merlin371 on 2011-08-16
> **ajs52698 said:**
> open jdk is sun java?

yes

and I dont know what else to tell ya about the package manager, are you still getting the same error?

---

### Post by ajs52698 on 2011-08-16
and now i cant install open jdk :( wtf?

---

### Post by TBABill on 2011-08-16
> **ajs52698 said:**
> Hello i have 2 problems.
 
The first synaptic package manager wont open when i try to open it i get this msg
 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 
Thats my first problem!
 
My second problem is i cant seem to find sun java6 in in ubuntu software center and i cant find any forums about it.
 
 
PLEASE HELP!
Did you open a terminal and type ```
sudo dpkg --configure -a
``` If not, do that first. Then open Software Sources and make sure you have enabled the Canonical Partner Repository. Then either click reload in Synaptic or go to a terminal and ```
sudo apt-get update
``` so it will pull in the list of all the new packages you have enabled in the repo. Once that is done, just go into Synaptic and search for Sun Java. If this is for your browser, just mark the Sun Java Plugin for installation, then click apply.

---

### Post by TBABill on 2011-08-16
> **merlin371 said:**
> yesNo, open jdk is not Sun Java. Open jdk is open source java while Sun Java is proprietary (and much better).

---

### Post by merlin371 on 2011-08-16
> **TBABill said:**
> No, open jdk is not Sun Java. Open jdk is open source java while Sun Java is proprietary (and much better).

orly?

[http://web.archive.org/web/20070517164922/http://www.sun.com/2006-1113/feature/story.jsp](http://web.archive.org/web/20070517164922/http://www.sun.com/2006-1113/feature/story.jsp)
OpenJDK was developed by Sun as well as the open source community, and as for the next java, openJDK is also gonna be the official one 

[http://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the](http://blogs.oracle.com/henrik/entry/moving_to_openjdk_as_the)

---

### Post by TBABill on 2011-08-16
Yep. Today the two are different. Open jdk is still not the same as the official Sun Java and does not perform as well. Until Java 7, they are separate and one outperforms the other. There are websites you can go to using open jdk (icedtea plugin) where java web performance is either degraded or impossible, but using the Sun Java plugin resolves most of those issues.

---

