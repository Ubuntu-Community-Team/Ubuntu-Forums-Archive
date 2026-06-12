---
title: "Howto: Install Chromium-browser nativly - not crossover"
date: 2009-07-21
forum: General Help
---

### Post by MadnessRed on 2009-07-21
It is now possible to run a native version of the Cromium browser. The open source version of Google Chrome. To do this is very simple


Simply add the following into you repositories. 
System > Administration > Software Sources > Third Party tab
Select add and add the following.
For Hardy or Intrepid users replace jaunty with the relevant options
```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```
```
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

Then go into symnaptic, select reload then install "chromium-browser"

It should then install fine.
Simple

---

