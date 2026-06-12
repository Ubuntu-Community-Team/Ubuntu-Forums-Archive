---
title: "Sun Java - Going Mad"
date: 2010-10-04
forum: General Help
---

### Post by Quarkrad on 2010-10-04
I'm having trouble installing sun java 6.  Keep trying, what I think, is the same thing e.g. 

*after issuing the "deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner" command, goto --> System --> administration --> software sources --> other software (tab) select(if already selected then reselect & select) the following sources,[url"]http://archive.canonical.com/ubuntu[/url] lucid partner" & " [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner" then close...it will ask whether you want to reload the packages...select reload" ,now issue "sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk"...now it will work*

Having done the above I type **java -version** in terminal and get:

[B]java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)[/B]

I've deleted everything java related via Synaptic, re booted, gone round in circles (I'm a newbie so getting use to this).  When I type **java -version** I'm looking for something that includes sun - the above terminal output looks to me I have not yet installed sun java 6

---

### Post by philinux on 2010-10-04
> **Quarkrad said:**
> I'm having trouble installing sun java 6.  Keep trying, what I think, is the same thing e.g. 

*after issuing the "deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner" command, goto --> System --> administration --> software sources --> other software (tab) select(if already selected then reselect & select) the following sources,[url"]http://archive.canonical.com/ubuntu[/url] lucid partner" & " [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner" then close...it will ask whether you want to reload the packages...select reload" ,now issue "sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk"...now it will work*

Having done the above I type **java -version** in terminal and get:

[B]java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)[/B]

I've deleted everything java related via Synaptic, re booted, gone round in circles (I'm a newbie so getting use to this).  When I type **java -version** I'm looking for something that includes sun - the above terminal output looks to me I have not yet installed sun java 6

That is sun java. Dont go mad.

Proof.
sudo update-java-alternatives -l
or
sudo update-alternatives --config java

---

### Post by andrewthomas on 2010-10-04
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Quarkrad on 2010-10-04
Many thanks :)

---

### Post by gandaran on 2010-10-04
> I've deleted everything java related via Synaptic, re booted, gone round in circles (I'm a newbie so getting use to this). When I type java -version I'm looking for something that includes sun - the above terminal output looks to me I have not yet installed sun java 6
I don't quite understand you problem, but if you want sun-java installed all you have to do is enable the archive.canonical partner repository in software sources and update the package list.
to install the java from the command line
```
sudo apt-get install sun-java6-plugin
```
and check that you haven't installed the openjdk-java or remove the open java, just use sun-java only

---

