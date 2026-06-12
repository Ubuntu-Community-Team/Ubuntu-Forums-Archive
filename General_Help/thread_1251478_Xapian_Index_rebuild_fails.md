---
title: "Xapian Index rebuild fails"
date: 2009-08-27
forum: General Help
---

### Post by jtappin on 2009-08-27
As of today, when I run adept I keep getting an error about failing to rebuild the Xapian index. By running the index updater from the command line I get the following error.
```
james@gabrielle:~/Data/Documents/Modelling$ sudo update-apt-xapian-index
[sudo] password for james:
Rebuilding Xapian index... 0%/usr/share/apt-xapian-index/plugins/apttags.py:104: DeprecationWarning: Accessed deprecated property Package.candidateRecord, please see the Version class for alternatives.
  rec = pkg.candidateRecord
/usr/share/apt-xapian-index/plugins/descriptions.py:75: DeprecationWarning: Accessed deprecated property Package.rawDescription, please see the Version class for alternatives.
  self.indexer.index_text_without_positions(pkg.rawDescription)
/usr/share/apt-xapian-index/plugins/sizes.py:74: DeprecationWarning: Accessed deprecated property Package.installedSize, please see the Version class for alternatives.
  instSize = pkg.installedSize
/usr/share/apt-xapian-index/plugins/sizes.py:75: DeprecationWarning: Accessed deprecated property Package.packageSize, please see the Version class for alternatives.
  pkgSize = pkg.packageSize
Rebuilding Xapian index... 2%
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 595, in <module>
    buildIndex(dbdir, addons, progress)
  File "/usr/sbin/update-apt-xapian-index", line 297, in buildIndex
    addon.obj.index(document, pkg)
  File "/usr/share/apt-xapian-index/plugins/descriptions.py", line 75, in index
    self.indexer.index_text_without_positions(pkg.rawDescription)
ValueError: invalid null reference in method 'TermGenerator_index_text_without_positions', argument 2 of type 'std::string const &'

```
It looks like an error in a python script somewhere, but I'm not sure which packages have broken it.

I'm runing Kubuntu Jaunty with the KDE 4.3 packages from the PPA. I did see some python related updates recently but I didn't look very carefully at them.

Does any apt or python guru have any ideas what's caused the breakage?

---

### Post by Partyboi2 on 2009-08-28
Hi, have you tried reinstalling the apt-xapian-index package?
```
sudo apt-get --reinstall install apt-xapian-index
```

---

### Post by jtappin on 2009-08-28
> **Partyboi2 said:**
> Hi, have you tried reinstalling the apt-xapian-index package?


I have now, and no change. 

The problem is now occurring on two machines, the only difference being that while my laptop fails at 2% of the rebuild, my desktop gets to about 30%.

My suspicion is that either python-apt or python-packagekit from the kubuntu PPA is incompatible with apt-xapian-index.

---

### Post by jtappin on 2009-08-28
> **jtappin said:**
> 
My suspicion is that either python-apt or python-packagekit from the kubuntu PPA is incompatible with apt-xapian-index.

The problem turns out to be python-apt 0.7.10 from the PPA with the KDE4 version of k3b ([http://ppa.launchpad.net/mieszkoslusarczyk/kde4-extras-kde4.3/ubuntu]("http://ppa.launchpad.net/mieszkoslusarczyk/kde4-extras-kde4.3/ubuntu")) which breaks the xapian scripts.

As a fix, I've disabled that repository and forcibly downgraded python-apt. But of course that has the drawback that now I won't get updates of the KDE4 k3b.

---

