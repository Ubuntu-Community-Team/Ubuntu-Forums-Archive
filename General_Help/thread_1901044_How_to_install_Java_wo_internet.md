---
title: "How to install Java w/o internet"
date: 2011-12-27
forum: General Help
---

### Post by n96 on 2011-12-27
Hello everyone!
I need help installing java. Every time I look up how to do it, people tell me to use terminal, but my Ubuntu 11.10 computer does not have an internet connection. My question is where can I find java for ubuntu (using a windows7 pc) to download onto a flash drive and install onto my ubuntu computer? Thanks very much beforehand.

---

### Post by sammiev on 2011-12-27
You can Download the [JRE Java]("http://sites.google.com/site/easylinuxtipsproject/java") file online and install it using this method without been online. :)

---

### Post by WorMzy on 2011-12-27
All packages available in the official repositories are available here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You may find it takes you a while to find the package you're looking for, as well as all the dependencies it requires, but unfortunately, that's the problem with having an offline PC. It's possible that you don't need to install any extra packages aside from the Java packages themselves, but in the case that you do need to install dependencies, you'll find them in the same place.

Good luck.

---

### Post by n96 on 2011-12-28
Ok so I downloaded a .jar file from the official repositories, placed it in my home folder and did sudo dpkg -I on it. It went ahead to do that, but now i'm stuck. Java doesn't seem to be installed yet and I don't know what the next step should be. Thanks again beforehand.

---

### Post by WorMzy on 2011-12-28
I don't think you downloaded a .jar from the official repositories. I think you probably mean a .deb. ;)

It might help if you told us which package you downloaded.

And I think the install command is dpkg -i, not dpkg -I. I'm not sure if the latter even does anything.

---

### Post by n96 on 2011-12-28
Oh my bad. It was a .deb. Filename is java-common_0.42ubuntu2_all.deb

---

### Post by WorMzy on 2011-12-28
Okay, that package doesn't install java itself, as you can see from the [list of files]("http://packages.ubuntu.com/oneiric/all/java-common/filelist").

The list of dependencies (or rather, *suggests*), has "[default-jre]("http://packages.ubuntu.com/oneiric/default-jre")". That package doesn't provide much either. However, that package depends on [default-jre-headless]("http://packages.ubuntu.com/oneiric/default-jre-headless"), and [openjdk-6-jre]("http://packages.ubuntu.com/oneiric/openjdk-6-jre"). You should probably install both of those too, although *again*, neither actually installs java. One of the dependencies of openjdk-6-jre though, is "[openjdk-6-jre-headless]("http://packages.ubuntu.com/oneiric/openjdk-6-jre-headless")", and this package, as far as I can tell, actually does *install* java.

But I can't guarantee it.

I'm afraid that Ubuntu's approach to packages leaves a lot to be desired.

---

### Post by n96 on 2011-12-29
Well I just downloaded default-jre, default-jre-headless, openjdk-6-jre (and the extremely long list of things it depends on, including openjdk-6-jre-headless). What do I do with them now? Do I just dpkg -i all of them or do I do something else?

---

### Post by WorMzy on 2011-12-29
```
dpkg -i *.deb
```

Will probably install them all in one go.

---

### Post by n96 on 2011-12-30
Thank you for all your help. After first downloading all the files for the wrong architecture (since apparently my computer is i386 even though it specifically states amd64 twice), then realizing I missed some files, java is finally working. Hurrah! You really don't appreciate Software Centre until you have to do this.

---

