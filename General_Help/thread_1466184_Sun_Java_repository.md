---
title: "Sun Java repository"
date: 2010-04-30
forum: General Help
---

### Post by erqiyang on 2010-04-30
Hi,

I just installed Ubuntu 10.04 into both my netbook and my desktop. After installing them, I installed the sun-java6-jre and sun-java6-jdk package from synaptic package manager on my netbook.

However, when i wanted to install the same package on my desktop, I realised the package is not in the package manager.

I've tried using apt-get install but it does not find the package as well.

Was wondering if anyone else encounter this as well. Anyone knows the fix to this?

P.s: I can still see the package on my netbook, which is running on UNR.

---

### Post by chessnerd on 2010-04-30
I noticed the same thing. It seems to have been removed from the repositories for some reason. Sun's website does offer the JRE and JDK for Linux so going here: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) should let you download what you need.

It's probably a blessing in disguise. Downloading anything from the repos right now takes FOREVER (been working on Eclipse for over half an hour, ugh...)

---

### Post by erqiyang on 2010-04-30
wow. I discovered the source of the problem. Literally.

Apparently, in the desktop version, if you want to install the sun-java6 package, you have got to add additional software sources. It can be added using the instruction as follow:

[LIST=1]
[*]System > Administration > Software Sources
[*]Under the tab "Other Software" click on the "Add" button.
[*]Enter "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner", without the quotes of course.
[*]Restart Synaptic. It will be there now...
[/LIST]

For some reason unknown, they've decided to leave out the source in the desktop version, but leave it in the UNR version...

---

