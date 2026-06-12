---
title: "Problem installing atunes"
date: 2009-09-26
forum: General Help
---

### Post by rmcellig on 2009-09-26
I am trying to install the audio player iTunes. I have the deb file but when I open it, the installer looks like Installer error enclosure. What should I do? When I open the Synaptic Package manager I get an error as well (see error enclosure. I also have a screenshot of my Software sources.

I am running 9.04

---

### Post by lamego on 2009-09-26
To fix the broken cache, open a terminal and run:
sudo apt-get install -f

The .deb that you are installing must have a missing dependency, just try to install it with: gdebi file.deb , it should report the problem.

---

### Post by rmcellig on 2009-09-26
Thanks so much! That worked great.

---

