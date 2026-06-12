---
title: "swiftfox uninstall"
date: 2009-09-19
forum: General Help
---

### Post by oboedad55 on 2009-09-19
Hi, I just installed swiftfox using a .deb file. I can't find a listing in synaptic to uninstall it and using apt-get remove swiftfox says there's nothing by that name. If I use apt-get remove swift* I get other things I don't want to remove. Thanks!

---

### Post by SoftwareExplorer on 2009-09-19
Do you still have the .deb or know what it's filename was? That might help you know what to remove.

---

### Post by oboedad55 on 2009-09-19
> **SoftwareExplorer said:**
> Do you still have the .deb or know what it's filename was? That might help you know what to remove.

Yes, I do. I found it by using aptitude search. It's called swiftfox-i686.

---

### Post by lovinglinux on 2009-09-19
Edit: nevermind.

---

### Post by seth.ammons on 2012-09-28
Hey all. I am having a problem uninstalling Swiftfox as well. I'm on 12.04. I have tried uninstalling both Swiftfox and Firefox and reinstalling Firefox. When I try to launch Firefox it comes up as Swiftfox.

How I got where I am:
added
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
to  /etc/apt/sources.list

apt-get update && apt-get install swiftfox-athlon64

# now, if I try to run Firefox, I get Swift fox. 
apt-get remove swiftfox-athlon64
apt-get remove firefox
apt-get install firefox

#firefox still comes up as swiftfox
apt-get remove firefox
aptitude purge swiftfox-athlon64

apt-get install firefox
# firefox still comes up as swiftfox

Any ideas? I have no idea where to go next.

---

