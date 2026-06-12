---
title: "Sun Java 6 Web Start Icon - Doesn't Work"
date: 2009-08-19
forum: General Help
---

### Post by terrance on 2009-08-19
When I go to applications - internet, I see an icon that says "sun java 6 web start". This appeared when I installed java through ubuntu's add/remove software program. When I click that icon however, it appears nothing happens. Is it normal for nothing to pop up? What's the purpose of the icon if it doesn't do anything?

---

### Post by t0p on 2009-08-19
What do you *want* to happen?

The way I run a java program is to type into the terminal something like:

```
java -jar somejavaprogram.jar
```

---

### Post by 3rdalbum on 2009-08-19
> **terrance said:**
> When I go to applications - internet, I see an icon that says "sun java 6 web start". This appeared when I installed java through ubuntu's add/remove software program. When I click that icon however, it appears nothing happens. Is it normal for nothing to pop up? What's the purpose of the icon if it doesn't do anything?

Don't worry. If Java is installed (and it is), then Firefox and Java-based applications will be able to use it. I have no idea what the Web Start menu item is for, and I don't recall it ever doing anything for me either.

---

### Post by daqron on 2010-05-16
WebStart is Sun's download manager. It's actually pretty cool, except that, infuriatingly, it doesn't work in Ubuntu 10.04. The OS and Firefox ought to be able to automatically launch WebStart for .jnlp files with no additional configuration (assuming Java is installed). 

To make it work properly, I had to do:
```
sudo update-alternatives --config javaws
```
Then select "/usr/lib/jvm/java-6-sun/jre/bin/javaws" as the default handler:
```
There are 2 choices for the alternative javaws (providing /usr/bin/javaws).

  Selection    Path                                        Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/javaws   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/javaws   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/javaws       63        manual mode
```
After I did that, it still didn't work automatically, but I was able to launch Java WebStart items by downloading the .jnlp file and entering at the terminal:
```
javaws filename.jnlp
```
Hope this helps some Googlers. This kind of stuff really needs to work out of the box. No regular user should have to know how to do this.

---

