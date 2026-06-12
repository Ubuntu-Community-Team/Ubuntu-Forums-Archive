---
title: "is the a way to download .deb parkage with its dependencies at once on using windows"
date: 2010-04-22
forum: General Help
---

### Post by elliotn on 2010-04-22
I was wondering if there is a trick to manipulate terminal in windows system to use the eg apt-get install gstreamer, what i exactly mean is I dont have internet and would like to install stuff but i always run into dependency problems. i use the internet cafe to download staff.

---

### Post by dineshs on 2010-04-22
From another ubuntu machine I think it is possible via Synaptic package manager.For this mark the package,go to file-generate package download script and save.Run the script from ubuntu M/c connected to net to download it to the same directory
Anyway I havent tried that

---

### Post by elliotn on 2010-04-22
> **dineshs said:**
> From another ubuntu machine I think it is possible via Synaptic package manager.For this mark the package,go to file-generate package download script and save.Run the script from ubuntu M/c connected to net to download it to the same directory
Anyway I havent tried that

there is no one i know that have am ubuntu machine in my place thus everyone uses windows.
The internet cafe is my last option

---

### Post by loell on 2010-04-22
try the [keryxproject]("http://keryxproject.org/")

---

### Post by dineshs on 2010-04-22
Let us wait for experts to answer.
There is a difficult way.You can use a live cd at the cafe .Then use the thumb drive containing script

---

### Post by dcstar on 2010-04-22
> **elliotn said:**
> I was wondering if there is a trick to manipulate terminal in windows system to use the eg apt-get install gstreamer, what i exactly mean is I dont have internet and would like to install stuff but i always run into dependency problems. i use the internet cafe to download staff.

Create an Ubuntu Live USB (with persistence) and boot the Internet Cafe PC off that.

---

### Post by nothingspecial on 2010-04-22
Or, very painstakingly, go [here]("http://packages.ubuntu.com/karmic/")

Then download each package and its dependencies, and its dependencies dependencies etc etc etc

---

### Post by elliotn on 2010-04-22
> **nothingspecial said:**
> Or, very painstakingly, go [here]("http://packages.ubuntu.com/karmic/")

Then download each package and its dependencies, and its dependencies dependencies etc etc etc

lol have been using that method but i keep missing one or 2 dependence as each dependence parkage depends on the other, so the list grows big

---

### Post by rahilm on 2010-04-22
IF you can get wget scripts to work in windows, i think it is possible.

---

### Post by sktsee on 2010-04-22
I haven't played with it myself, but it looks like [Apt-offline]("http://www.debian-administration.org/article/Offline_Package_Management_for_APT") might fit the bill.

---

### Post by john newbuntu on 2010-04-22
If you extend dineshs's (post #2) idea with rahilm's idea(post #9) using "gnu wget" that is available for windows, it might make your task a bit simpler with some minor tweaking:

[http://gr33ndata.blogspot.com/2007/06/wget-and-dos-for-loop.html](http://gr33ndata.blogspot.com/2007/06/wget-and-dos-for-loop.html)

You can google for wget for dos and perhaps find some other utility to help you download files on windows.

---

### Post by elliotn on 2010-04-22
> **john newbuntu said:**
> If you extend dineshs's (post #2) idea with rahilm's idea(post #9) using "gnu wget" that is available for windows, it might make your task a bit simpler with some minor tweaking:

[http://gr33ndata.blogspot.com/2007/06/wget-and-dos-for-loop.html](http://gr33ndata.blogspot.com/2007/06/wget-and-dos-for-loop.html)

You can google for wget for dos and perhaps find some other utility to help you download files on windows.

that souns promIsing

---

### Post by donsy on 2010-04-22
> **rahilm said:**
> IF you can get wget scripts to work in windows, i think it is possible.
Cygwin has a wget package: [http://www.cygwin.com/packages/](http://www.cygwin.com/packages/)

---

