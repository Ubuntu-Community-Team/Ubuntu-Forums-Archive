---
title: "this must be easy : install geogebra?"
date: 2010-04-13
forum: General Help
---

### Post by peter_kint on 2010-04-13
Hi,
I want to install geogebra.
It's here [http:///www.geogebra.org/cms/]("http://www.geogebra.org/cms/")
I go to downloads, there's 2 options:[INDENT]1. WEBSTART: clicking on this throws me on a 'Java Downloads for LInux' page ([http://java.com/en/download/linux_manual.jsp?host=java.com&returnPage=http://www.geogebra.org/webstart/geogebra.jnlp&locale=en-US](http://java.com/en/download/linux_manual.jsp?host=java.com&returnPage=http://www.geogebra.org/webstart/geogebra.jnlp&locale=en-US)

2. APPLET START: clicking on it gives me the error message "Sorry, the GeoGebra Applet could not be started. Please make sure that  Java 1.4.2 (or later) is installed and activated.([click here to install Java now]("http://java.sun.com/getjava"))"
[/INDENT]Apparently something is wrong with my Java, but when I check in synaptic JDK seems to be installed, and[INDENT]j```
ava -version
```[/INDENT]gives me:[INDENT]```
 java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18~pre4-1ubuntu1)
OpenJDK Server VM (build 16.0-b13, mixed mode)
```[/INDENT]How do I get Geogebra working?

---

### Post by philinux on 2010-04-13
I have exactly same java installed, 64 bit mind, and the applet runs fine.

---

### Post by peter_kint on 2010-04-13
> **philinux said:**
> I have exactly same java installed, 64 bit mind, and the applet runs fine.

Thats good for you! :-)
But how do I get mine working?

---

### Post by Martje_001 on 2010-04-13
I think you should remove OpenJDK and give the 'official' java package a try. It's called sun-java6-jre.

Btw: GeoGebra is a pretty good program!

---

### Post by peter_kint on 2010-04-13
> **Martje_001 said:**
> I think you should remove OpenJDK and give the 'official' java package a try. It's called sun-java6-jre.

Btw: GeoGebra is a pretty good program!

Indeed! I am a math teacher and I just love GeoGebra. I encourage them kids to use it.

However, I am a linux beginner and a bit afraid to mess things up (I've already got some baaaad experiences...) . My searches on this forum and google  have not resulted in consistent/comprehensible info.

1. Remove JDK = mark everything with 'jdk' in synaptic and remove it?
2. Install sun java = some command with 'sudo apt-get' in a terminal?
3. And Geogebra install?

It would really make my day

---

### Post by Martje_001 on 2010-04-13
> **peter_kint said:**
> Indeed! I am a math teacher and I just love GeoGebra. I encourage them kids to use it.
Ok! I'm a student and I have to use it regularly.

> **peter_kint said:**
> 1. Remove JDK = mark everything with 'jdk' in synaptic and remove it?
That's a good approach.

> **peter_kint said:**
> 2. Install sun java = some command with 'sudo apt-get' in a terminal?
That's fine, but you can also use Synaptic. Just search for 'jre' and the right packages will show up!

---

### Post by peter_kint on 2010-04-13
Thx for the answer, but I have exactly the same problems.

Here is my java version, the GeoGebra site seems to think I have no Java...[INDENT]```
peter@peter-desktop:~$ java -version
java version "1.6.0_19"
Java(TM) SE Runtime Environment (build 1.6.0_19-b04)
Java HotSpot(TM) Server VM (build 16.2-b04, mixed mode)
peter@peter-desktop:~$ 
```[/INDENT]Any ideas anyone? Is there another way I can get GeoGebra installed?

---

### Post by philinux on 2010-04-13
> **peter_kint said:**
> Thx for the answer, but I have exactly the same problems.

Here is my java version, the GeoGebra site seems to think I have no Java...[INDENT]```
peter@peter-desktop:~$ java -version
java version "1.6.0_19"
Java(TM) SE Runtime Environment (build 1.6.0_19-b04)
Java HotSpot(TM) Server VM (build 16.2-b04, mixed mode)
peter@peter-desktop:~$ 
```[/INDENT]Any ideas anyone? Is there another way I can get GeoGebra installed?

Just double check your firefox prefs.

Edit>prefs>Content tab. Java enabled

Also try FF in safe mode. Close FF open a terminal

```
firefox -safe-mode
```

An addon might be the problem.

---

### Post by peter_kint on 2010-04-13
> **philinux said:**
> Just double check your firefox prefs.

Edit>prefs>Content tab. Java enabled

Also try FF in safe mode. Close FF open a terminal

```
firefox -safe-mode
```An addon might be the problem.

Alas! Exacte the same errors/problems again.
On top of that, I get this when I close firefox:

[INDENT]peter@peter-desktop:~$ firefox -safe-mode
(firefox-bin:1859): Gdk-WARNING **: XID collision, trouble ahead
peter@peter-desktop:~$ 
[/INDENT]Looks cloudy...

---

### Post by peter_kint on 2010-04-13
Hello,
I found the solution myself : I forgot to install the java-PLUGIN
The GeoGebra applet is working like a train now.

peter

---

