---
title: "Java issue in karmic or FF 3.5?"
date: 2009-12-14
forum: General Help
---

### Post by knottshawk on 2009-12-14
I use a Java based VPN for work... on my 8.10 system it works relatively smooth. I recently got a new system with 9.10 and can't get the VPN to work at all... 

Both systems are using JRE6... but the 9.10 system fails to operate the Java applet properly both in Firefox and in Epiphany

---

### Post by Mighty_Joe on 2009-12-14
What version of Java are you using on each system?
```
java -version
```

---

### Post by knottshawk on 2009-12-14
```
On 9.10 - 
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)

On 8.10
java version "1.6.0_14"
Java (TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot (TM) Server VM (build 14.0-b16, mixed mode)
```


It should be noted that I wasn't using OpenJDK on 9.10 earlier, and still had the problem

Without OpenJDK it's:
```
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.1-b02, mixed mode)
```

---

### Post by knottshawk on 2009-12-14
Found [This thread]("http://ubuntuforums.org/showthread.php?t=1314202") that seems to be good for updating Java... problem is that when I ran the 64 bit instructions, Java installs fine but doesn't fix my VPN. I did note that Sun, on the download page for Java has this disconcerting statement:

> * Please use the 32-bit version for Java applet and Java Web Start support. 

Well, I'm on 64 bit Karmic... and if I try to use the 32 bit version it either fails, or I'm doing it wrong.... Ideas?

---

### Post by knottshawk on 2009-12-15
Any ideas? Need help!

---

### Post by knottshawk on 2009-12-17
One more cry for help here...

---

### Post by xifer on 2009-12-17
> **knottshawk said:**
> Found [This thread]("http://ubuntuforums.org/showthread.php?t=1314202") that seems to be good for updating Java... problem is that when I ran the 64 bit instructions, Java installs fine but doesn't fix my VPN. I did note that Sun, on the download page for Java has this disconcerting statement:



Well, I'm on 64 bit Karmic... and if I try to use the 32 bit version it either fails, or I'm doing it wrong.... Ideas?

How does it fail?  I'm not a 64-bit user but I think if you completely remove java and then install the 32-bit it should work.

---

### Post by knottshawk on 2009-12-17
Well, when I followed the instructions in that thread (the one I linked to above) and try to install the 32 bit version on my 64 bit system, it doesn't install...I mean maybe it fails at the point of linking it to FireFox... that's why I'm wondering if it's something simple, like, I'm wondering which path name I should use since I'm on 64 bit, but the java package is expecting a 32 bit path?

---

### Post by xifer on 2009-12-17
sorry not to be more help, but if the 32-bit install DID work ok - and I'd like to see the log of the install to be sure, then if you type 

```
about:plugins
``` into firefox location bar - what does it say for java?

and if you search your system for the plugin is it found?

try this

cd /
find . -name libjavaplugin* -print 2>/dev/null

create a link in ~/.mozilla/plugins to the required library

---

### Post by knottshawk on 2009-12-17
Okay, after the 32 bit install there is nothing listed in about:plugins.. that's what I meant by it fails to install in Firefox... 

Output from find . -name libjavaplugin* -print 2>/dev/null 
```
./home/me/.mozilla/plugins/libjavaplugin_oji.so
./home/me/.mozilla/libjavaplugin_oji.so
./home/me/Downloads/jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so
./home/me/Downloads/jre1.6.0_17/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
./home/me/Downloads/jre1.6.0_17/lib/i386/libjavaplugin_nscp_gcc29.so
./home/me/Downloads/jre1.6.0_17/lib/i386/libjavaplugin_nscp.so
./home/me/Downloads/jre1.6.0_17/lib/i386/libjavaplugin_jni.so
./opt/java/32/jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so
./opt/java/32/jre1.6.0_17/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
./opt/java/32/jre1.6.0_17/lib/i386/libjavaplugin_nscp_gcc29.so
./opt/java/32/jre1.6.0_17/lib/i386/libjavaplugin_nscp.so
./opt/java/32/jre1.6.0_17/lib/i386/libjavaplugin_jni.so
``` 

The tutorial says to link the plugin to FireFox via this:
```
ln -s /opt/java/32/jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```
compared with the 64 bit Java instructions:
```
ln -s /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

```
But I'm wondering if the 64 bit version of FF is okay with that.. I mean, obviously not :(

---

### Post by xifer on 2009-12-18
> **knottshawk said:**
> But I'm wondering if the 64 bit version of FF is okay with that.. I mean, obviously not :(


Seems not, if you created the link ok - and can see it in the directory, restart ff and it is still not visible in the plugins page then how bout trying the 32-bit version of firefox?

---

### Post by knottshawk on 2009-12-18
> **xifer said:**
> Seems not, if you created the link ok - and can see it in the directory, restart ff and it is still not visible in the plugins page then how bout trying the 32-bit version of firefox?

Yeah.... I may have to try that.

---

