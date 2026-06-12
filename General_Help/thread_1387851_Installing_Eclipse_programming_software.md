---
title: "Installing Eclipse programming software"
date: 2010-01-22
forum: General Help
---

### Post by teward on 2010-01-22
Got an issue when installing Eclipse.

Eclipse installs its own JDK over Sun Java and it screws with ```
java
javac
```
and every IDE that I use.

Need 100% accurate instructions please for installing Eclipse.

---

### Post by teward on 2010-01-22
bump

---

### Post by teward on 2010-01-22
bump

---

### Post by gerryg001 on 2010-01-23
Not using Jaunty, but I've got it running in Karmic and Hardy (for several years). There have been some problems with other than Sun Java, so I've installed it each time. Where are you getting which Eclipse from? Dist or website download? If latter, which one? I downloaded Eclipse Classic for Hardy, installed Sun Java. For Karmic, I used the dist. You didn't mention which workbench, as some have some special needs. I don't know where your java change is coming from, unless it's a dependency on a distribution. Even then, though, you can change it.

If downloading Eclipse, I've recently had issues with other than Classic, but that may not relate to your issue.

---

### Post by Maheriano on 2010-01-24
I downloaded Eclipse from the package manager and it was the wrong one for developing Java. I had to go to their website and download the specific package from there. Then I got it working but I have noticed my online videos haven't worked the same, not sure if they're related.

---

### Post by ChrisB111 on 2010-01-24
Have you had a look at the ubuntu wiki page about eclipse, I found it useful when trying to get it to run under ubuntu.

Chris

LINK: [EclipseIDE - Community Ubuntu Documentation]("https://help.ubuntu.com/community/EclipseIDE")

---

### Post by gerryg001 on 2010-01-24
Well, you're missing any detail needed to say any more. Take a look at the url that Chris mentioned, and the links inside. That looks pretty complete for Eclipse/Java.

---

### Post by GregBrannon on 2010-01-24
TC, I'm running OpenSUSE, so what I'm about to say may be totally useless, but I don't think so.  It seems to me that it should work the same for any linux OS.

If you haven't already, install Sun's JDK 6.

The Eclipse packages downloaded from the Eclipse Download site ([http://www.eclipse.org/downloads/]("http://www.eclipse.org/downloads/")) are written totally in Java, essentially source files, but no:KSt the kind that you have to compile and then build to work on your specific platform.  You simply download the Eclipse distribution file of your choice, uncompress it into a directory you have control of (usually 'eclipse' off of your home root directory), preserving the directory structure, and run the executable file "eclipse" that will then exist in the directory you uncompressed the files into.

You can then build a "shortcut" to that file.   If you're running under KDE, you should include the line:

export GDK_NATIVE_WINDOWS=true

before calling the eclipse executable to resolve an issue with eclipse dialogue and menu buttons not always responding correctly to mouse clicks.

It's very simple, works great, and I love Eclipse.

---

### Post by teward on 2010-01-24
Sorry for a very long response time, i've been quite busy repairing computers all day :P

Anyways, what I did was install Eclipse from the repos (Applications -> Add/Remove).

What it did was install some random java compiler that caused issues with my terminal java commands.

I'll take a look at the link, see what it says, and get back to you all.

---

### Post by teward on 2010-01-25
Well, I downloaded the eclipse .tar.gz file from their site, installed it manually to /myHome folder under /myHome/eclipse-ide

Got it all working, thanks for the links, now I need the JDK 5 and JDK 6 (my instructors for programming are hard-*** about it)

---

### Post by Maheriano on 2010-01-25
> **Maheriano said:**
> I downloaded Eclipse from the package manager and it was the wrong one for developing Java. I had to go to their website and download the specific package from there.
> **TrekCaptainUSA said:**
> Anyways, what I did was install Eclipse from the repos (Applications -> Add/Remove).Didn't I just say not to do this? Did you read my post?

> **TrekCaptainUSA said:**
> Well, I downloaded the eclipse .tar.gz file from their site, installed it manually to /myHome folder under /myHome/eclipse-ide

Got it all working, thanks for the links, now I need the JDK 5 and JDK 6 (my instructors for programming are hard-*** about it)There you go.

---

### Post by teward on 2010-01-26
> **Maheriano said:**
> Didn't I just say not to do this? Did you read my post?

There you go.


final thought on this:

Initially, installing from the repos is what messed Java and javac.

I already fixed this.

---

