---
title: "How to install Java on LUBUNTU 10.04"
date: 2010-05-06
forum: General Help
---

### Post by SILLAT on 2010-05-06
How do you install Java on Lubuntu 10.04 ? ?

I've been trying out Lubuntu 10.04 but i haven't been able to find any quick start tutorial on how to install essential programs like java runtime,flash,codecs,etc. i use ubuntu so i was able to get in flash an the codecs (gstreamer) but i need some advice on java.

Thanks in advance

---

### Post by SILLAT on 2010-05-06
After waiting hours for a reply to my question, i took to Google again to search how to install java on lubuntu 10.04 and this time i had a lil luck :) 

Found the release notes here: [https://wiki.kubuntu.org/Lubuntu/ReleaseNotes/LucidLynx](https://wiki.kubuntu.org/Lubuntu/ReleaseNotes/LucidLynx)

It stated:
For lubuntu 10.04 LTS, the sun-java6 packages have been dropped from the Multiverse section of the lubuntu archive. It is recommended that you use openjdk-6 instead.

If you can not switch from the proprietary Sun JDK/JRE to OpenJDK, you can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line:

     sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

I installed the latter & seems fine so far if it does not work out i'll be moving back to the recommended openjdk-6 instead )

):P

---

### Post by pvossen on 2010-05-07
No luck here installing the sun-java6-jre files. I am
trying to get Jdk and the IcedTea that goes with it to run
two of my java programs that always worked in JRE. So far
no such luck.

---

### Post by spinlock99 on 2010-06-09
Any idea why Canonical is not recomending sun's java? Is this a philosophical/legal issue or are there system integration/performance issues to consider?

Thanks

---

### Post by tomdavidson on 2010-06-12
pvossen: i you have a different JRE already installed, then you need to selected the default environment - [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

As SILLAT pointed out, sun-java6* has been moved in the the partner repo rather than the universe (not sure i understand that decision).  So just enable the partner repo and after an update you will see the Sun packages.

spinlock99: im wonder if it has something to do with the changes in the Ubuntu/Redhat relationship, but mostly likely it was influenced by OpenJava's recent compliance certification.

---

### Post by gigo625913 on 2010-06-15
I am new user.I managed to install and get java work with Firefox 3.6.3.Packages installed:
[B]openjdk-6-jdk
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea-6-jre-cacao
icedtea6-plugin
[/B]

Note: I find it very hard to get it work. This is a totally mess for a new user to get this simple thing done.

---

### Post by philinux on 2010-06-15
```
sudo apt-get install ubuntu-restricted-extras
```

Would do the job. 

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by Bluenateman on 2013-02-03
> **philinux said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```Would do the job. 

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

This is what worked for me after my puny brain tried for three days to figure it out. Thank you to Philinux!

---

