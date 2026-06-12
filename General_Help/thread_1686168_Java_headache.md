---
title: "Java headache"
date: 2011-02-11
forum: General Help
---

### Post by frank cox on 2011-02-11
According to the terminal I have :
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.5) (6b20-1.9.5-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)

It also says I have it installed in Synaptic but when I try to test it or use it to play onling games nothing.

I had to make some links in Puppy Linux to get it to work there but it is much more complicated in Ubuntu, at least for me.

---

### Post by GregBrannon on 2011-02-12
Some recommend removing OpenJDK and installing the Sun/Oracle JDK/JRE.

---

### Post by wojox on 2011-02-12
To install (Sun) Java in Ubuntu 10.10 Maverick Meerkat you'll have to enable the Partner repository: open Ubuntu Software Center and go to Edit > Software Sources, then on the "Other Software" enable the Partner repository (it should be the first on the list; it looks like this: "http://archive.canonical.com/ubuntu maverick partner".).

Then, click "Close" and when asked, click "Reload" and finally install Sun Java6 in Ubuntu 10.10 by searching for it in Ubuntu Software Center.

---

### Post by frank cox on 2011-02-12
> **wojox said:**
> To install (Sun) Java in Ubuntu 10.10 Maverick Meerkat you'll have to enable the Partner repository: open Ubuntu Software Center and go to Edit > Software Sources, then on the "Other Software" enable the Partner repository (it should be the first on the list; it looks like this: "http://archive.canonical.com/ubuntu maverick partner".).

Then, click "Close" and when asked, click "Reload" and finally install Sun Java6 in Ubuntu 10.10 by searching for it in Ubuntu Software Center.

Thanks for the reply!
My bad-I am using 10.04 and the Partner repository is activated.

---

### Post by wojox on 2011-02-12
Okay do this:

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”
```

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by frank cox on 2011-02-13
That is how I installed it and it says its there. java -version brings up 1.6 in terminal but none of the Java testers see it and the games won't play-Pogo etc.

Thanks

---

### Post by Miyavix3 on 2011-02-13
It sounds like your path variable is set to openJDK.

check to see if you have java installed. (probably in your /usr/jre* folder)

If you do, you can add /usr/jre*/bin to your path variable or I guess you can type /usr/jre*/bin/java every time you want to invoke java.

---

### Post by nmaster on 2011-02-13
if you need a java plugin for your web browser, this is the package you need to install:
icedtea6-plugin

---

### Post by asmoore82 on 2011-02-13
You need a separate package for the java browser plugin.
For OpenJDK, this package is called "icedtea6-plugin"

---

