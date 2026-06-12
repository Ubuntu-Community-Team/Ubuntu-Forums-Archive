---
title: "How to instalk Mozilla Firefox?"
date: 2009-09-14
forum: General Help
---

### Post by ChaosChris2009 on 2009-09-14
I've tried via Konsole, sudo app-get install firefox, no luck, though

Any ideas?

I've got the .tar on my desktop, oh, and 9.04

Just installed Kubuntu today

EDIT: Typo in thread title, meant to say install, not instalk, sorry about that

---

### Post by abyrne on 2009-09-14
Could you clarify a little bit on that? What was the output of sudo apt-get firefox?

---

### Post by ankspo71 on 2009-09-14
Hi, you almost had it.

it is:
sudo **apt**-get install firefox

Using this will download and install firefox for you, so you don't actually need the tar.gz file you downloaded to your desktop.

PS, if you were looking for Firefox 3.5
I'm pretty sure the line in the terminal would be

sudo apt-get install firefox-3.5

---

### Post by ChaosChris2009 on 2009-09-14
> **ankspo71 said:**
> Hi, you almost had it.

it is:
sudo **apt**-get install firefox

Using this will download and install firefox for you, so you don't actually need the tar.gz file you downloaded to your desktop.

Tried that as well, the result is below

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

---

### Post by DasEi on 2009-09-14
Repositories enabled ? System updated ?

---

### Post by ChaosChris2009 on 2009-09-14
> **DasEi said:**
> Repositories enabled ? System updated ?
How do I know if repositories are enabled?

Updating atm

---

### Post by DasEi on 2009-09-14
either by synaptic (system > prferences) or by editing /etc/apt/sources.list;; make sure the "#" in the line of wanted repos is deleted

ff : firefox (source: firefox-3.0): meta package for the popular mozilla web browser. In component main, is optional. Version 3.0.14+build2+nobinonly-0ubuntu0.9.04.1 (jaunty), package size 67 kB, installed size 124 kB

---

### Post by aysiu on 2009-09-14
> **ChaosChris2009 said:**
> How do I know if repositories are enabled?

Updating atm I think you should read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by ChaosChris2009 on 2009-09-14
> **ankspo71 said:**
> Hi, you almost had it.

it is:
sudo **apt**-get install firefox

Using this will download and install firefox for you, so you don't actually need the tar.gz file you downloaded to your desktop.

PS, if you were looking for Firefox 3.5
I'm pretty sure the line in the terminal would be

sudo apt-get install firefox-3.5

I was about to go bananas, seriously, but I unfortunately ended up with 3.0.14, instead of 3.5.3

How do I end up getting 3.5?

Anyone?

---

### Post by sports fan Matt on 2009-09-14
Try looking here :) [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by xebian on 2009-09-14
> **ChaosChris2009 said:**
> I was about to go bananas, seriously, but I unfortunately ended up with 3.0.14, instead of 3.5.3

How do I end up getting 3.5?

Anyone?

```
ii  firefox-3.0    3.0.14+build2+nobinonly-0ubuntu1          
ii  firefox-3.0-branding  3.0.14+build2+nobinonly-0ubuntu1         
ii  firefox-3.5          3.5.3+build1+nobinonly-0ubuntu2          
ii  firefox-3.5-branding 3.5.3+build1+nobinonly-0ubuntu2           

```

install any of the package named above

---

### Post by holycow131415 on 2009-09-14
go to your add/remove, and look for sherktio (sp?) or abrowser 3.5. both are firefox 3.5.2

---

