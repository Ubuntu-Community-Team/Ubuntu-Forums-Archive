---
title: "Jdownloader debian package?"
date: 2010-04-27
forum: General Help
---

### Post by msit.ce on 2010-04-27
1) Is there any debian package for jdownloader. It's a fantastic DM but due to java based, it reduces the net speed. :(

2) Is there any other DM like jdownloader but not java based?

---

### Post by nechus on 2010-05-02
There's a deb package you can download and install, but it's an old version: [http://www.mediafire.com/?gcgfezmcjiw](http://www.mediafire.com/?gcgfezmcjiw)

A very easy way to install JDownloader in Ubuntu is to copy the two following lines and paste them in a terminal:
First:
sudo add-apt-repository ppa:jd-team/jdownloader

(Press Enter)

Then:
sudo apt-get update && sudo apt-get install jdownloader

(Press Enter)

By the way, this method will keep you updated with any new versions of JDownloader. Isn't it fantastic??

Enjoy!

---

### Post by msit.ce on 2010-05-03
> **nechus said:**
> 

A very easy way to install JDownloader in Ubuntu is to copy the two following lines and paste them in a terminal:
First:
sudo add-apt-repository ppa:jd-team/jdownloader

(Press Enter)
After giving that command it shows...............
> sudo: add-apt-repository: command not foundThanx for ur mediafire link. But is that deb package of Jdownloader Java Based?

---

### Post by nechus on 2010-05-03
Oops!  Then you can go to [https://launchpad.net/~jd-team/+archive/jdownloader](https://launchpad.net/~jd-team/+archive/jdownloader) and click on the green text "Technical details about this PPA" and follow the instructions. :P

I don't know much about programming languages, so I can't say if a program is Java-based or not. Sorry! :(

Let me know if you are able to install JDownloader from the PPA. :popcorn:

---

### Post by karma coma on 2010-10-06
This instruction totally worked fine for me, after i installed Java. Thanks for explaining.

---

### Post by soldier1st on 2010-10-07
Jdownloader is Java based which will work with either sun java or openjdk and there is one that is similar but it tends to be flakey and that is Tucan and currently there is nothing similar to jdownloader although if there was one i myself would like it to be non java as java eats memory.

---

