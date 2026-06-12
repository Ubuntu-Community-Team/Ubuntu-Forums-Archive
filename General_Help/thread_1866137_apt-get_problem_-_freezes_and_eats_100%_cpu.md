---
title: "apt-get problem - freezes and eats 100% cpu"
date: 2011-10-21
forum: General Help
---

### Post by eXt on 2011-10-21
Hi!

   I've a strange problem with apt-get. It started few days ago when I noticed that system update notifier is using 100% cpu. Each time I start my computer I have to manually kill apt-check.py and similiar processes that eat 100% cpu. 

I narrowed this down to be a problem with apt-get, because:
1. notifier I, mentioned above, calls apt-check.py (and probably apt-get) to check updates
2. synaptic freezes and consumes 100% cpu when I try to update a package
3. apt-get dist-upgrade freezes eating 100% cpu

However I can still use apt-get update and apt-get upgrade from console. 

What's more: apt-get upgrade reports that there are "blocked" packages (for example kadu) and apt-get install kadu also freezes apt-get and consumes my cpu.

Any hints?

---

### Post by marusz on 2011-10-26
Remove "patryk-prezu-ppa-maverick.list" file from "/etc/apt/sources.list.d"

Use this command: sudo rm patryk-prezu-ppa-maverick.list

---

