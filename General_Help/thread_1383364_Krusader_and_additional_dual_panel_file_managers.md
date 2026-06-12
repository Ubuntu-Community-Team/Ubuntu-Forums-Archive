---
title: "Krusader and additional dual panel file managers"
date: 2010-01-17
forum: General Help
---

### Post by Kermit524 on 2010-01-17
Hi,
Krusader crashes immediately on start-up at Karmic.
This is new. Only changes to my system lately was a routinal FSCK while booting.
This is the error message I get:
"Application: Krusader (krusader), signal: Segmentation fault
[KCrash Handler]
#6  0x0808aa88 in _start ()"

I thought about trying to reset Krusader's settings. Problem is: I don't know where to locate them. I would expect a .krusader folder unde my home dir, but it's nowhere to be found.

Any idea what can be done to fix this? I have no clue what to do next...

Many thanks in advance,
Michal

---

### Post by Kermit524 on 2010-01-18
Ok - I have finally managed to find the configuration file:
~/.kde/share/config/krusaderrc
Renamed it and everything is on the go.
For further reference:
[http://www.krusader.org/handbook/config_files.html](http://www.krusader.org/handbook/config_files.html)

---

