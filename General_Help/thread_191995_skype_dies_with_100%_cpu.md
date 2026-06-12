---
title: "skype dies with 100% cpu"
date: 2006-06-08
forum: General Help
---

### Post by trollzor on 2006-06-08
Skype, both from the .deb and the static qt compiled .tar.gz, will start, let me enter username and password but will then stop responding and eat 100% cpu. Fresh install of Dapper on a machine where skype worked in hoary and in dapper flight 5.

Started it in a terminal, no special output or messages, just a crash.

Does anyone else have skype working?

---

### Post by thasheep on 2006-06-08
I use the skype from the breezy-seveas repo. For some reason it isn't in the dapper one but this works fine. Add the following line to /etc/apt/sources.list```
deb http://seveas.theplayboymansion.net/seveas breezy-seveas extras
```Then do```
sudo apt-get update
sudo apt-get install skype-dsp-hijacker
```The dsp-hijacker fixes problems to do with sound in skype being shit.

---

