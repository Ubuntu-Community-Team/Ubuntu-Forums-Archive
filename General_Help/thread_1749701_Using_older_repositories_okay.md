---
title: "Using older repositories okay?"
date: 2011-05-04
forum: General Help
---

### Post by olwe on 2011-05-04
I'd like to use an older repository. I'm on Lucid10.04 and the repository is for gutsy 7.0. It's a bunch of gimp brushes. These are the lines I'm supposed to add to sources.list:

deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gutsy main

Seems iffy... Advice?

---

### Post by Dr. Nick on 2011-05-04
Dont :P

You can try to download and install the .deb files for the brushes and see if it gives you dependency issues when you install, but I would not add the repos to your source file. Are you sure the brushes are compatible with the gimp in 10.04?

---

