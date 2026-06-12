---
title: "Synaptic/Mudlet install issues"
date: 2011-04-17
forum: General Help
---

### Post by EmilyRose on 2011-04-17
Hi there, so I'm trying to get Mudlet and despite all my efforst I've failed. Sort of. It will actually install, only I get a couple errors.

First of all, after checking the 'mark for installation' box I get a notice/error/warning about liblua5.1-rex-pcre0 (version 2.4.0-1) being "Not Authenticated" I say OK, and it goes on to try to install. And then I get this: 

An error occurred: 
> E: /var/cache/apt/archives/liblua5.1-rex-pcre0_2.4.0-1_i386.deb: trying to overwrite '/usr/lib/lua/5.1/rex_pcre.so', which is also in package lrexlib1 2.4.0-1~ppa17


Now, at this point, Mudlet has actually succesfully installed and is functional. The only problem is that I am no longer able to do system updates and/or install anything else... cause I get errors about the aforementioned liblau5.1-rex-pcre0. 

The only way to do get them to go away is to uninstall mudlet. Which as I admit to loving... is a bit on the obnoxious side. Anybody have any thoughts/suggestions??

---

### Post by Vadi on 2011-04-18
Remove the lrexlib1 package, and if it's not happy then, reinstall Mudlet.

---

### Post by EmilyRose on 2011-04-19
That worked! Thank you!! Don't know why I didn't think of that.. duh :p

---

