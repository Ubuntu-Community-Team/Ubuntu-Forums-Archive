---
title: "Burn Packages?"
date: 2009-12-20
forum: General Help
---

### Post by stepstools on 2009-12-20
I was wondering if there was a way to burn .deb packages to CD-ROM.

---

### Post by tuahaa on 2009-12-20
I believe there's an app that called "APTonCD" which can be installed in Ubuntu

With this cool app (that I have yet to use), you can burn all your already installed deb software and put it on a CD- this way if you want to transfer software from one computer to another, or just need to back up all your current stuff, APTonCD will do it for you. To install it, you can search for it in the software centre or in synaptic. Alternatively, if you are comfortable in with the command line, you can go to terminal and enter this:

```
sudo apt-get install aptoncd

```

I'm also guessing that there is a directory for individual deb packages that you have downloaded. But I suggest you explore APTonCD...

---

### Post by stepstools on 2009-12-20
Not quite what I was looking for.  Something to create CD's to give to my Linux friends so they could install the software, without having to install APTonCD.  Even though, this app is pretty cool.  It will help when I plan to do a clean install when 10.04 comes around.

---

### Post by dcstar on 2009-12-20
> **stepstools said:**
> I was wondering if there was a way to burn .deb packages to CD-ROM.

Many packages have dependencies, so unless you have all of those also available it can be pointless having individual .deb packages on a CD - although you can (just like any other file).

---

