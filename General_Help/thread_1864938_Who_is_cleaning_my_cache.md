---
title: "Who is cleaning my cache?"
date: 2011-10-19
forum: General Help
---

### Post by vikash_chandola on 2011-10-19
Packages of all those software that i install through software center are saved in var->cache-> archives. A week ago it was aroud of size 320MB but now it is 130MB where does rest of packages go. It seems they are deleted. But who is deleting them is it settings of synaptic. I put a screen shot of synaptic->preference it is set to not delete any package. If it is so then who is deleting those packages.

---

### Post by gmargo on 2011-10-19
Probably someone ran "apt-get clean" or "aptitude clean" (or whatever the gui offers for clean).  /var/cache/apt/archives is not a great place to "save" your files, as it is only meant to be temporary.

A much better choice for preserving your downloaded *.deb files is to run the **apt-cacher-ng** daemon, and set up your **apt** configuration to go through that server.

[http://packages.ubuntu.com/oneiric/apt-cacher-ng](http://packages.ubuntu.com/oneiric/apt-cacher-ng)

---

### Post by Slim Odds on 2011-10-19
> **gmargo said:**
> Probably someone ran "apt-get clean" or "aptitude clean" (or whatever the gui offers for clean).  /var/cache/apt/archives is not a great place to "save" your files, as it is only meant to be temporary.

A much better choice for preserving your downloaded *.deb files is to run the **apt-cacher-ng** daemon, and set up your **apt** configuration to go through that server.

[http://packages.ubuntu.com/oneiric/apt-cacher-ng](http://packages.ubuntu.com/oneiric/apt-cacher-ng)

Agree with your first point. Any directory/data below a directory named "*cache*" is, by definition, volatile and transient.

---

