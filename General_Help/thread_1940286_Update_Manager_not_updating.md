---
title: "Update Manager not updating"
date: 2012-03-13
forum: General Help
---

### Post by latinlightning on 2012-03-13
Hello guys,

I used to have a problem before with my PC at home with a similar issue. This time I need assistance with my work PC. I haven't been able to get Update Manager to update my system for the last twelve days. I remember the issue with my PC was related to a PPA so perhaps this is similar? I tried disabling a couple, but that has not helped.

I have attached a couple of screen shots of what I'm currently experiencing:

---

### Post by howefield on 2012-03-13
Try disabling the Wine repositories.

---

### Post by latinlightning on 2012-03-13
It would probably help to take a snapshot of the exact source :popcorn:

---

### Post by latinlightning on 2012-03-13
> **howefield said:**
> Try disabling the Wine repositories.

I disabled both Wine PPA's and that only gave me the same results:

---

### Post by latinlightning on 2012-03-13
One update went through and installed after disabling another PPA yet Update Manager keeps saying it's been 12 days since I last installed updates. I know before this started happening, when I would get updates on my home machine (running Ubuntu 11.04 as well) I knew the day after I would get pretty much the same ones the day I would walk into work on my work PC. That is not the case anymore . . .

---

### Post by howefield on 2012-03-13
Might be worth backing up your sources.list and generating a fresh one from here..

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by latinlightning on 2012-03-13
> **howefield said:**
> Might be worth backing up your sources.list and generating a fresh one from here..

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

I unchecked every item under the Other Software tab in the **Software Sources** list and then had just *Canonical Partners* and *Canonical Partners (Source Code)* checked. The machine then showed that it was finally up-to-date. Running apt-get update even showed no more errors. I started checking each item on the list one at a time and was able to pin point it to the *[http://ppa.launchpad.net///ubuntu](http://ppa.launchpad.net///ubuntu) natty main* and *[http://ppa.launchpad.net///ubuntu](http://ppa.launchpad.net///ubuntu) natty main* *(Source Code)* .

Are those last two really necessary to keep the system as secure and stable as possible? I want to make sure before performing the fresh sources.list procedure.

---

### Post by howefield on 2012-03-13
Those lines look wrong with the 3 forward slashes.

Where did they come from ?

---

### Post by latinlightning on 2012-03-13
> **howefield said:**
> Those lines look wrong with the 3 forward slashes.

Where did they come from ?

My guess is as good as yours. If there's something there that I can do please advise. Greatly appreciate the support thus far!

---

