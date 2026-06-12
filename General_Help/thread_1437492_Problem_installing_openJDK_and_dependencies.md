---
title: "Problem installing openJDK and dependencies"
date: 2010-03-24
forum: General Help
---

### Post by tenmilez on 2010-03-24
My situation is that I have access to the internet, but not on my laptop where I have ubuntu installed because I'm deployed to Afghanistan. What I have done is downloaded the debs that I need from the repos (packages.ubuntu.com), copy them to a flash drive, and install them on my laptop from there. However, when I come across the package **openjdk-6-jre-lib **it depends on **openjdk-6-jre-headless **and **openjdk-6-jre-headless **depends on **openjdk-6-jre-lib** so I can't install either without installing the other first. How do I work around this so that I can finish installing these packages? Also, I'm running Karmic UNR.

---

### Post by houseworkshy on 2010-03-24
That sounds like an old fashioned "dependancy hell" and I don't know the answer.  However, if your stick is big enough you could try putting an installation of Ubuntu on the stick itself then boot directly into it when you get to the online machine and install things in the usual ways.  If the online machine also has Ubuntu a package like AptonCd could be handy too

---

### Post by tenmilez on 2010-03-24
Unfortunately there is no way to get Ubuntu online out here because it's all government networks and they get antsy about that kind of thing. I can use windows to access the internet and save stuff to a USB and that's it. 

It still bugs me though because there should be a way to install these packages even if they depend on each other. I know it works somehow because I can apt-get to install it at home where I do have the internet and it works without a hitch.

---

### Post by houseworkshy on 2010-03-24
Understood, I hadn't concidered that angle which is fair enough when one thinks about security.  ( avoids strong temptation to bash windows at this point )  Well you could simply use java, it's not open source but it is free and does work.
P.S. I hope you get home safe btw.  Irrespective of politics, most are aware that it boils down to people suffering and hope for peace.

---

### Post by tenmilez on 2010-03-24
Apparently the solution is ```
sudo dpkg -i –force-depends *.deb
``` executed from within the directory that has the debs. I found it on a website that gives a tutorial for Keryx which solves my other issue: downloading packages with their dependencies. 

[Keryx]("http://keryxproject.org/")
[Tutorial]("http://crashsystems.net/2009/01/keryx-tutorial/")

---

