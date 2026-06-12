---
title: "Driver problem after accidently uninstalling something"
date: 2010-12-22
forum: General Help
---

### Post by JezzaFromAUS on 2010-12-22
Hey I was going through installing alot of things from the Software Centre, and when I went to install a certain thing it said that I needed to uninstall some things, I clicked install anyways and it then made some errors all the things installing failed and it was saying something like apt-get install -f to fix the problem. Anyways so now I can't seem to put the appearance on full and I think that it's missing important system files or drivers, is there a way that I can check for missing or corrupt system files and fix them without removing all my programs? Thanks and sorry I'm new to Ubuntu.

---

### Post by oldos2er on 2010-12-22
Can you run **sudo apt-get install -f** in a terminal, and if there are errors post the output here?

---

### Post by JezzaFromAUS on 2010-12-23
Hey thanks,

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 libpng12-dev linux-headers-2.6.35-22-generic
  libjpeg62-dev zlib1g-dev libtiff4-dev libtiffxx0c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

---

### Post by oldos2er on 2010-12-23
So the package manager appears to be working correctly...? I don't understand what you mean by "I can't seem to put the appearance on full". If you're having video resolution problems, please post with your hardware details.

---

### Post by JezzaFromAUS on 2011-02-07
woops, how to delete a thread.

---

