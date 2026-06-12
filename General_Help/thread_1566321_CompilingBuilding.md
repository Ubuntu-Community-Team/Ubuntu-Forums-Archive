---
title: "Compiling/Building"
date: 2010-09-02
forum: General Help
---

### Post by jameshampshire on 2010-09-02
alright so ive had ubuntu for awhile.
i know how to install deb files cause its simple its just a self installer.
but i still dont understand how to compile things.
i downloaded this [http://hyperglitch.com/dev/VocProc/](http://hyperglitch.com/dev/VocProc/)
i saved the file to my desktop i read the readme and i still dont get it.
somebody help me please.

---

### Post by leg on 2010-09-02
This how to is a must read:

[Building and installing how to]("http://tldp.org/HOWTO/Software-Building-HOWTO.html")

Make sure you build dependencies installed so that you have the compiler installed. The next one is from the Ubuntu community docs

[Building on Ubuntu]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by jameshampshire on 2010-09-02
WOAH that seems like alot of work.
why dont they just make all files deb files.
would make life alot easier.

---

### Post by lykeion on 2010-09-02
On the VocProc homepage they actually have links for deb files and a PPA repository. (See the links under the News header)
You can easily add the PPA repository by following the instructions on the page:
[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

But since the PPA also contains 60 other applications, you might just want to download the deb file manually and install only that one. 
Here are the links for the VocProc deb files:

VocProc Standalone
[https://launchpad.net/~philip5/+archive/extra/+files/vocproc_0.12.2-lucid%7Eppa1_i386.deb](https://launchpad.net/~philip5/+archive/extra/+files/vocproc_0.12.2-lucid%7Eppa1_i386.deb)

VocProc LV2 Plugin
[https://launchpad.net/~philip5/+archive/extra/+files/vocproc-lv2_0.2-lucid%7Eppa1_i386.deb](https://launchpad.net/~philip5/+archive/extra/+files/vocproc-lv2_0.2-lucid%7Eppa1_i386.deb)

(Note these are for Lucid i386. If you run Karmic or amd64 you'll have to find the appropriate debs yourself)
> **jameshampshire said:**
> WOAH that seems like alot of work.
why dont they just make all files deb files.
would make life alot easier.

I guess the reason why not everyone supply deb files, 
is that Ubuntu/Debian is not the only distribution out there.
Compile and build from source can be done on all linux dist.

---

### Post by jameshampshire on 2010-09-02
thanks heaps mate

---

