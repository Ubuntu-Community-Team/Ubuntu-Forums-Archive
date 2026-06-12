---
title: "List of packages installed with Lubuntu?"
date: 2012-04-12
forum: General Help
---

### Post by reset042 on 2012-04-12
I'm disappointed with the way parts of Ubuntu have been going and seem to be headed, so I'm looking at alternatives. Lubuntu looks promising, but before installing it I'd like to know a list of packages and services that are installed by default. Is there a list anywhere?

---

### Post by raja.genupula on 2012-04-12
yeah we have a list 
[http://en.wikipedia.org/wiki/Lubuntu#Applications](http://en.wikipedia.org/wiki/Lubuntu#Applications)

---

### Post by reset042 on 2012-04-13
Thank you Raja. Sorry, but I should have phrased my question better. I think I meant to ask what processes or services are included by default with Lubuntu. Specifically, I do not want an operating system with things like Zeitgeist installed by default. I'd like to review a list of such services before deciding to install.

---

### Post by ankspo71 on 2012-04-13
I haven't found a complete package list for Lubuntu online, but if you have already downloaded and burned a copy of Lubuntu "desktop" cd to try it out, then you can boot into a live session use this command to generate a complete list of installed packages.

```
dpkg --get-selections > ~/Desktop/packages.txt
```

Lubuntu comes with Synaptic Package Manager installed too, so you can also open Synaptic and search for specific packages, or simply sort the first column, the column that indicates the installed and upgrade-able packages.

I am using Lubuntu 12.04 beta now, and it looks like zeitgeist was never installed.

---

### Post by wojox on 2012-04-13
[Ubuntu -- Details of package lubuntu-desktop in precise]("http://packages.ubuntu.com/precise/lubuntu-desktop")

That may help narrow it down. Zeitgeist is all Gnome.

---

