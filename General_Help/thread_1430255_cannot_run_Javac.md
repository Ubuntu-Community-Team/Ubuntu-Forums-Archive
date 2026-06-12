---
title: "cannot run Javac"
date: 2010-03-15
forum: General Help
---

### Post by mosty friedman on 2010-03-15
hey everyone,

I just upgraded to ubuntu 9.10 from 9.04, however when i try to compile a java program i get this 

> 
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found


even though i already have sun-java6-jdk installed and it worked fine in 9.04..i even checked to see if maybe it got removed during the upgrade or something but no its still there.. anyone got an idea of how to go about this??

---

### Post by byStanderone on 2010-03-15
...try installing the parser generator:

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=javac](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=javac)

---

### Post by Mighty_Joe on 2010-03-15
The Sun Java package is in a transitional state in Karmic.  First it was frozen in the repository with the intent to remove it in favor of OpenJDK.  Now it looks like it will be moved to the [partner repository]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/420426") for Lucid.  
What this means for you is that upgrading from Jaunty to Karmic causes havoc because the package in Karmic is older than the one in Jaunty. Your best bet may be to remove all the existing Java packages and reinstall them.  
If you want the current version of Sun Java, [this]("http://sites.google.com/site/easylinuxtipsproject/java") is currently the best way to get it.

---

### Post by byStanderone on 2010-03-16
...thanks mighty_joe, learned a new one from you.

---

### Post by mosty friedman on 2010-03-27
thanks for the reply guys, and sorry for my late reply but i actually resolved this seconds after i made this thread..I did what you said mightyjoe, i reinstalled the java packages and it worked fine..thanks again everyone

---

