---
title: "various repos gone belly-up"
date: 2011-10-06
forum: General Help
---

### Post by HappyLinux on 2011-10-06
I found a major problem, and I don't know if it's my end or the repositories.

Originally, I'd been having a problem with a website that requires JavaRuntime to handle forms etc. LoveFilm is the website. Well, I thought the problem was their end, so I got in touch with them and they said that their site uses Java a lot and that maybe my browser needs updating.

However, seeing as I'm using the latest versions of FF, Chrome and Opera, I don't see it being a browser problem. So I thought that maybe it was the JavaRuntime that's install.

Upon routing round a little, I found that I have OpenJDK 6 installed with its corresponding Tea program. However, there OpenJDK 7 has been released for a few months, and seeing as I don't actually need the JRE from Oracle directly, I tried to update OpenJDK.

This is where I noticed something major.

I went routing through Synaptic Package thingy and found that OJDK7 is not listed, only version 6. So browsing the internet, I managed to find the launchpad repository for it and to to put it into Synaptics. However, upon hitting refresh, I noticed that it was struggling when checking the repositories.

90% of every repository failed. In each repository, you have the main program, perhaps a dictionary, maybe an add-on or two. However, the vast bulk simply failed. There were a few listed as hits, and even fewer listed as done.

I don't know if the OpenJDK one failed or not, but I removed it from the list.

Is this a problem that's my end? Do I need to redo the repository links in synaptics? or is it a problem with the repos themselves?

---

### Post by thatguruguy on 2011-10-06
[http://ubuntuforums.org/showthread.php?t=1855292](http://ubuntuforums.org/showthread.php?t=1855292)[URL="http://ubuntuforums.org/showthread.php?p=11315723"]
[/URL]

---

### Post by HappyLinux on 2011-10-06
But what about the other problem.

Oh yes, I just tried running sudo "apt-get install --reinstall icedtea-plugin openjdk-7-jre" from the futuredesktop link and got this

```
simon@simon-linux:~$ sudo apt-get install --reinstall icedtea-plugin openjdk-7-jre
[sudo] password for simon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package openjdk-7-jre
simon@simon-linux:~$ 

```

---

