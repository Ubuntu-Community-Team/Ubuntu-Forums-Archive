---
title: "Help downloading only w/ apt-get"
date: 2010-01-15
forum: General Help
---

### Post by clevertomato on 2010-01-15
I know apt-get has a switch to make it download only. Then, I guess the packages can be installed later using dpkg -i ?   But...


[LIST=1]
[*]Where are the packages put when using apt-get to download only? Can I specify where to put them when I use the apt-get command?
[*]What if there are required packages to meet dependencies?... are they stored in the same place automatically? If I install later using dpkg, do I have to explicitly install the dependency packages or will they be pulled in from the same directory automagically at the time of install?
[/LIST]

---

### Post by mikewhatever on 2010-01-15
> **shawnboy said:**
> I know apt-get has a switch to make it download only. Then, I guess the packages can be installed later using dpkg -i ?   But...


[LIST=1]
[*]Where are the packages put when using apt-get to download only? Can I specify where to put them when I use the apt-get command?

[*]What if there are required packages to meet dependencies?... are they stored in the same place automatically? If I install later using dpkg, do I have to explicitly install the dependency packages or will they be pulled in from the same directory automagically at the time of install?
[/LIST]

/var/cache/apt/archives

Dependencies are also downloaded to the same location, and yes, you'll have to explicitly install them.

---

### Post by clevertomato on 2010-01-15
Thanks, mikewhatever.

---

