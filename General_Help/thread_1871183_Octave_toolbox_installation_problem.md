---
title: "Octave toolbox installation problem"
date: 2011-10-28
forum: General Help
---

### Post by stallinux on 2011-10-28
Encountered a problem in the installation of toolboxes of Octave. Since I also found the solution I thought I'd share it with you so that if you also find this problem one day you will rapidly Google your way to the solution. (I often find solutions myself here on this forum).

Problem: toolbox <x> in Octave installed but not working
Ubuntu 11.04 32 bit Classic desktop
Octave 3.2.4
Example: symbolic manipulation toolbox
> symbols
error: 'symbols' undefined near line 1 column 1

Solution:
1) In Synaptic Package Manager: install 'octave3.2-headers'
2) On-line: at SourceForge: download 'symbolic-1.1.0.tar.gz'
3) In Octave (sudo octave): type 'pkg install symbolic-1.1.0.tar.gz'

This will compile and install the package correctly (takes some time), after which you can use it in Octave:
> pkg load symbolic  (not needed, I guess)
> symbols

etc.

---

### Post by nardis_Miles1 on 2012-05-25
Thanks for this quick tutorial.

So, does this mean that the ubuntu packages for various octave toolkits are non-functional? Why are they in the repository?

---

