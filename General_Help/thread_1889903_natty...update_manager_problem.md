---
title: "natty...update manager problem"
date: 2011-12-02
forum: General Help
---

### Post by amarocktht on 2011-12-02
E: Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/tualatrix-ppa-natty.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

this error is displayed...when try to open update manager...update manger,synaptic manager is jammed...help me out..peoples:(.

---

### Post by matt_symes on 2011-12-02
Hi

ain should be main. I think this is your error.

Open a terminal and type (or copy and paste)

```
sudo sed -i 's/ain/main/g' /etc/apt/sources.list.d/tualatrix-ppa-natty.list
```Enter your password. It will not be echoed to the screen. Then type

```
sudo apt-get update
```Any errors, post back and we'll have a closer look at the problem.

Kind regards

---

