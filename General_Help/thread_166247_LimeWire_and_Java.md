---
title: "LimeWire and Java"
date: 2006-04-26
forum: General Help
---

### Post by frup on 2006-04-26
i installed limewire in opt as given by easylinux.info for ubuntu
when i run runLime.sh through terminal i get this message
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
laurent@ubuntu:/opt/LimeWire$

(through gui doesnt do anything at all)
i have done

laurent@ubuntu:~/Desktop$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-gcj/bin/java' to provide `java'.
laurent@ubuntu:~/Desktop$   sudo update-alternatives --config jar

There are 2 alternatives which provide `jar'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/fastjar
*+    2        /usr/lib/jvm/java-gcj/bin/jar

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-gcj/bin/jar' to provide `jar'.

trying to get it to work....  any ehlp is apreaciated

---

### Post by Mr Green on 2006-04-26
You need to install Sun's Java:

[http://my.opera.com/Mr%20Green/blog/show.dml/189036](http://my.opera.com/Mr%20Green/blog/show.dml/189036)

---

### Post by frup on 2006-04-26
i thought i had... downloaded the bin.

chomd X and ran it...

after that i tried converting it into a .deb aswell and installing it :S.... still no luck :(

---

### Post by Efwis on 2006-04-26
[QUOTE=frup]i thought i had... downloaded the bin.

chomd X and ran it...

after that i tried converting it into a .deb aswell and installing it :S.... still no luck :([/QUOTE]
if you install sun's JRE through automatix  and then choose that as your default java install using the 
```
sudo update-alternatives --config java
```
It will work

---

