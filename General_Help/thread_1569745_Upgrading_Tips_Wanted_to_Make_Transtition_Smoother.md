---
title: "Upgrading: Tips Wanted to Make Transtition Smoother"
date: 2010-09-07
forum: General Help
---

### Post by DrDevice on 2010-09-07
Hello!  Just looking for a piece of advice on my next Ubuntu project.  I'm going to upgrade.  Yes!  How exciting!

:confused:

No worries, what I mean is that instead of a clean install, I want to try and use the upgrade feature just to see how well it works.  I'm moving from 9.04 to 10.04.  In this regard, I'm looking for some common pitfalls to avoid, tips to make the transition smoother, etc.

To start us out, I've used dpkg to output a list of all my currently installed packages, and have backed up my home directory; I'm not betting the farm on this working, better safe than sorry.

Let 'em rip, and thanks for your time!

---

### Post by zvacet on 2010-09-07
If you want to upgrade you have to do it like this Jaunty>Karmic>Lucid,because you can not skip release.Be sure that your Jaunty is up-to-date with

```
sudo apt-get update && sudo apt-get upgrade
```

After that you can upgrade with updates manager.Repeat same procedure to go from Karmic to Lucid.

---

### Post by DrDevice on 2010-09-20
> **zvacet said:**
> If you want to upgrade you have to do it like this Jaunty>Karmic>Lucid,because you can not skip release.

Exactly what I thought would have to happen.  And to be honest, when I saw that it would take 4-5 hrs to complete just the basic upgrade downloads (for both), I said "no way!" and did a clean install.

Conclusions for my impromptu experiment:  It's faster to clean install and configure then to upgrade.

Thank you for your input!

---

