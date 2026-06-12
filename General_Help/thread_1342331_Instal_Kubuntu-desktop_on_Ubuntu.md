---
title: "Instal Kubuntu-desktop on Ubuntu"
date: 2009-11-30
forum: General Help
---

### Post by Telhma on 2009-11-30
Hello all, i know in previous version of Ubuntu, you could download with the synaptic packet manager the Kubuntu desktop to use the KDE-4 environment.

but now i can't see it in the search any more when i use the packet manager. do somebody know how i can install it, without the need of make a dual boot?

thanks in advance

---

### Post by NoaHall on 2009-11-30
From the terminal - 
```
sudo apt-get install kubuntu-desktop --no-install-recommends
```
Notice the case. The no install recommends is there to stop it downloading a load of stuff you don't need.

---

### Post by wilee-nilee on 2009-11-30
Try looking with kubuntu-desktop or run in the terminal.
sudo apt-get install kubuntu-desktop

---

### Post by mkvnmtr on 2009-11-30
It is listed in the first meta packages section.

---

### Post by Telhma on 2009-11-30
Oh, thanks for the fast awnsers, I did a search, but no hits, i will try that command in the terminal, thanks a lot ;)

if it's not working, you will hear it :)

kisses

---

