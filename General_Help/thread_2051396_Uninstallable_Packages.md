---
title: "Uninstallable Packages"
date: 2012-09-01
forum: General Help
---

### Post by zerubbabel on 2012-09-01
I'm trying to install LibreOffice 3.6.1 from the LibreOffice launchpad repositories, but get the message in the attached screenshot. Even if I uncheck these repositories and try to reinstall the 3.5.4 version from the standard ubuntu repositories, I get a similar error. Obviously something is broken, but I don't know what or how to fix it.

---

### Post by ajgreeny on 2012-09-01
What happens if you try to do the installation with ```
sudo apt-get install libreoffice
```or perhaps using synaptic?  I am aware that synaptic is no longer a default part of ubuntu, and has not been in kubuntu for even longer, I think, but I am also aware that whatever is the default in kubuntu, it can not be as good as synaptic, which in my opinion is unbeatable.

PS:  I assume you have updated the repos after making any changes to your software sources?

---

### Post by drmrgd on 2012-09-01
> **ajgreeny said:**
> <snip>

PS:  I assume you have updated the repos after making any changes to your software sources?

That was my first thought as well.  I'm not sure why installing from the launchpad repo is not working.  However, for the older version in the Kubuntu repos, I would (after removing the Libre Office repo) run:

```
sudo apt-get clean && sudo apt-get update
```

Then try to get Libre Office again.

---

### Post by Arbayong on 2012-09-01
i suspect u have a dependency issue. install synaptic package manager. select install packages option on the left side of the screen and use the search box near the top centre part of the screen to search for libreoffice.

u'll find a list of libreoffice products currently install on ur system. mark all of them for complete removal and remove them.
run sudo apt-get update to refresh ur repos

try installing libreoffice package again either via synaptic or terminal. u can also try the launchpad repo.

its advisable to do a smart upgrade of ur system b4 installing libreoffice

---

### Post by zerubbabel on 2012-09-01
> **Arbayong said:**
> i suspect u have a dependency issue. install synaptic package manager. select install packages option on the left side of the screen and use the search box near the top centre part of the screen to search for libreoffice.

u'll find a list of libreoffice products currently install on ur system. mark all of them for complete removal and remove them.
run sudo apt-get update to refresh ur repos

try installing libreoffice package again either via synaptic or terminal. u can also try the launchpad repo.

its advisable to do a smart upgrade of ur system b4 installing libreoffice

Ok, I'll try this, but what do you mean by a "smart upgrade of your system"?

---

### Post by zerubbabel on 2012-09-04
Well, after trying everything recommended, I ended up having to reinstall Kubuntu from scratch. But here is the sequence that led to the trouble: 

1) Add the libreoffice ppa to the softwares sources
2) Run the Update Manager
3) Elect to install LibreOffice 3.6.0
4) After installation, the Update Manager shows the message in the attached screen shot.
5) Click Ok to remove the marked packages, as suggested.
6) LibreOffice is no more. 
7) Try to install LibreOffice again, but it fails saying that the packages identified in step 5 are "uninstallable."
8) Couldn't find any way past this point.

So, after reinstalling Kubuntu, I repeated steps 1 through 4, but declined to do step 5, that is, remove the marked packages. 

So now LibreOffice 3.6.0 runs fine. I still get the message of step 4 every time I run the Update Manager, unless I disable the LibreOffice ppa.

Anyone have any idea what is going on?

---

