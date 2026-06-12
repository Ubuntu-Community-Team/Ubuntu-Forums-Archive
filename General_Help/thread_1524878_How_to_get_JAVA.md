---
title: "How to get JAVA?"
date: 2010-07-05
forum: General Help
---

### Post by Cam! on 2010-07-05
It has come to my attention that Ubuntu doesn't come equipped with Java. I can't use Runescape, or other Java-run things. How do I get Java? I went on Software Center and DL'd OpenJava 6, but that doesn't do anything.

---

### Post by donsy on 2010-07-05
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by Cam! on 2010-07-11
That didn't work at all. I even went as far as to DL "OpenJDK" from the Package manager, but sites like RuneScape didn't work.

---

### Post by HenneBaby02 on 2010-07-11
Im new to ubuntu myself... and i havent played runescape but if it runs off of java do what "donsy" said java JDK is for development ... Java JRE is what u need for java based programs... u can search jre and look for sun-javajre (or something like that) in the package manager, for me anyways the package manager didn't work well and i was still runnin JDK.. if that happens to u remove sunjavaJRE and try installing it from Terminal.. if that doesn't work u can do it the long way by downloadin from the site directly

---

### Post by HenneBaby02 on 2010-07-11
ok i found this maybe it can help... 


[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

try that link, its for ubuntu 7.10 but i mean it should still work the same on later versions, That link explains how to install both java JDK and JRE or to switch between JDK and JRE

EDIT: I forgot about the edit button lol sry to post basically the same thing twice

---

### Post by DougieFresh4U on 2010-07-11
> **donsy said:**
> sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts

After you add the repo,(with out the quotes) and save and close sources, you need to issue:
```
sudo apt-get update
```
than you can issue:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by cazador31 on 2010-07-11
Go here. this will install Java

Scroll down and use the quick method. Then scroll down and install the 33 or 64 bit

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by JustinR on 2010-07-11
Or you could go to Java's website and download it from there.

---

### Post by Queue29 on 2010-07-11
> **JustinR said:**
> Or you could go to Java's website and download it from there.

That will just complicate things even more. Setting up the plugins by hand is a PITA, and is pointless when there are .deb packages set up to do exactly that.

---

### Post by Jakiejake on 2010-07-11
Get google chrome and follow this
[http://www.chromedocs.net/2010/06/or-how-i-learned-to-stop-reading-bug.html](http://www.chromedocs.net/2010/06/or-how-i-learned-to-stop-reading-bug.html)
That should help!

---

### Post by Simdog1 on 2010-07-14
i get
E: Couldn't find package sun-java6-bin

---

### Post by oldos2er on 2010-07-14
Enable the partner repository (System, Administration, Software Sources).

---

### Post by nmaster on 2010-07-14
you need the firefox java plugin right? its called Iced Tea.  its in the repos. you don't need to mess around with stuff from sun or different browsers.  Iced Tea is meant to work with firefox.

---

### Post by belkinsa on 2010-07-14
I didn't find it in the repos.   I only found tea.

---

### Post by nmaster on 2010-07-14
> **Mechafish said:**
> I didn't find it in the repos.   I only found tea.

try enabling all of the available repositories.  here is the info on the package.  its definitely there somewhere. 
[http://packages.ubuntu.com/lucid/icedtea6-plugin](http://packages.ubuntu.com/lucid/icedtea6-plugin)

---

### Post by libssd on 2010-07-14
> **donsy said:**
> sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts

Worked for me; the only difference being that after I added the new repository from the command line, I installed the sun-java packages using Synaptic -- I like to read the descriptions before installing packages.

Re repositories, what's the difference (if any) between these two:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

More generally, how do you know what a repository is for (other than guessing from its name)?

---

### Post by belkinsa on 2010-07-14
Turns out that I have that...sorry for replying this topic.  I having java problems on one site, so I need to ask them no you guys.  Oppps....

---

### Post by nmaster on 2010-07-14
> **Mechafish said:**
> Turns out that I have that...sorry for replying this topic.  I having java problems on one site, so I need to ask them no you guys.  Oppps....

if the problem is with the website, try using a different browser and see what happens.

---

