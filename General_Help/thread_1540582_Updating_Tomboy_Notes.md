---
title: "Updating Tomboy Notes"
date: 2010-07-28
forum: General Help
---

### Post by blue carrot on 2010-07-28
Hi guys,

I'm running the old original version of Tomboy Notes (1.0.0). 

I'm using it quite a bit for my masters thesis and I'm keen to upgrade it to the most recent version incase there are functionality improvements that will help me with my work.

Unfortunatley, I'm too retarded to actually know how to update this software and have all my old notes transferred to the new version. 

I tried downloading the new version, but it wouldn't install because it said Tomboy is already installed. I tried deleting orginanl tomboy but then I couldn't even install the new one.

Clearly I'm a person of windows level intelligence attempting to run a linux system. Any help would be appreciated.

---

### Post by sharm on 2010-07-28
I'll let an Ubuntu guy answer the best way to get a newer package, but before you get to eager, take a look at the new features in Tomboy 1.2.0 and make sure there are features or fixes that you care about:

[http://lists.beatniksoftware.com/pipermail/tomboy-list-beatniksoftware.com/2010-March/001553.html](http://lists.beatniksoftware.com/pipermail/tomboy-list-beatniksoftware.com/2010-March/001553.html)

---

### Post by chopinhauer on 2010-07-28
> **blue carrot said:**
> 
I tried downloading the new version, but it wouldn't install because it said Tomboy is already installed. I tried deleting orginanl tomboy but then I couldn't even install the new one.


To force the reinstallation of Tomboy type in a terminal:
```
sudo apt-get --reinstall install tomboy
```
(you could probably do it with the GUI, but I'm not accustomed to it)

Distributions rarely give multiple versions of the same software for the same release, unless security problems arise (or other important updates). An exception is the 'backports' software repository, which you can activate in your Software Sources.

Assuming you are still using Jaunty Jackalope the [last version available](http://packages.ubuntu.com/search?keywords=tomboy&searchon=names&suite=all&section=all) is 0.14.0-0ubuntu1, while for Karmic Koala it's 1.0.0-0ubuntu2.

The [Tomboy Packagers Team](https://launchpad.net/~tomboy-packagers) on Launchpad publishes a software repository (PPA repository) with [version 1.0.1](https://launchpad.net/~tomboy-packagers/+archive/stable) available for both Jaunty and Karmic: the instruction on how to add the repository are on [Launchpad](https://launchpad.net/~tomboy-packagers/+archive/stable).

I think the easiest way for you to obtain the new Tomboy version is to upgrade your distribution to Lucid Lynx, but since you are writing your master's thesis, I don't think you are eager to do it. The alternative is to compile the software yourself. It is not difficult, but it requires some time and patience.

---

