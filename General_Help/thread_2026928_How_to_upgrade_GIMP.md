---
title: "How to upgrade GIMP?"
date: 2012-07-16
forum: General Help
---

### Post by HackTec on 2012-07-16
Hello guys.
I am new here,and also new with the Ubuntu OS.

I just installed Ubuntu 11.10 and heard about GIMP,and on their official site the latest version is 2.8,but I got 2.6 and my question is how do I upgrade from GIMP 2.6 to GIMP 2.8? Thanks!

---

### Post by kmsalex on 2012-07-16
[https://launchpad.net/~rbose-debianizer/+archive/gimp](https://launchpad.net/~rbose-debianizer/+archive/gimp)

Why didn't you install 12.04?

---

### Post by raja.genupula on 2012-07-16
[COLOR=#c20cb9]** **[/COLOR]http://maketecheasier.com/upgrade-to-gimp-2-8-in-ubuntu/2012/05/04

---

### Post by kmsalex on 2012-07-16
> **raja.genupula said:**
> [COLOR=#c20cb9]** **[/COLOR]http://maketecheasier.com/upgrade-to-gimp-2-8-in-ubuntu/2012/05/04

That guide is for 12.04, the one i provided is supposed to be 11.10 compatible.

---

### Post by HackTec on 2012-07-16
@kmsalex What am I supposed to do with that link?I see it's a PPA,but I don't know how to add it and install the gimp package from it.
I didn't installed 12.04 cause I tried and got video driver problems.

@raja.genupula That method didn't worked for me ,I still got the 2.6 version :( .

---

### Post by kmsalex on 2012-07-16
Did you try install video drives on 12.04??? or just starting from scratch and trying a second time? 12.04 is supported much longer, and has had a lot of performance improvements, in a year or 2 it will be hard to get things like this to install as people stop bothering to support it.

First do a 

```
sudo apt-get purge gimp
```

you want to type that into a terminal (search for terminal in the dash)

I've provide a screen shot for installing... this is a community willing to help but you should give it some effort as well ;)

---

### Post by HackTec on 2012-07-16
@kmsalex Thanks alot,but it didn't worked too.
I added [B]ppa:rbose-debianizer/gimp to my ppa's,after executing the purge command,then ran sudo apt-get update .Afterwards,i tried to sudo apt-get install gimp,but it's still 2.6 :(.
[/B]

---

### Post by kmsalex on 2012-07-16
> **HackTec said:**
> @kmsalex Thanks alot,but it didn't worked too.
I added [B]ppa:rbose-debianizer/gimp to my ppa's,after executing the purge command,then ran sudo apt-get update .Afterwards,i tried to sudo apt-get install gimp,but it's still 2.6 :(.
[/B]

Honestly I couldn't tell you what to do, I've got it running fine on 12.04, being its not a LTS (long term stable) like 12.04 with time this problem will only get worse.

What exactly was your problem with 12.04? 

Have you tried some of the sister distributions?

[Kubuntu]("http://www.kubuntu.org/") uses kde for the desktop, might be a little more fermilure to a windows user 

[Xubuntu]("http://xubuntu.org/") using xfce for the desktop and should be a bit liter on the system

---

