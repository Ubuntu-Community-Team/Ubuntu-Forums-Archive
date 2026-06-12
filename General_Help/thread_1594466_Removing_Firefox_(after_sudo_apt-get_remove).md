---
title: "Removing Firefox (after sudo apt-get remove)"
date: 2010-10-12
forum: General Help
---

### Post by skytreader on 2010-10-12
Hi. I sudo apt-get removed Firefox from my system in favor of Google Chrome. However, Ubuntu still prompts me to upgrade Firefox. How do I stop that?

Also, whenever I click on HTML files, Firefox is still the one that loads by default. How can that be if I've sudo apt-get removed it?

And Firefox is still in my Applications->Internet menu...

So, was my sudo apt-get remove successful?

---

### Post by Chesamo on 2010-10-12
I don't know how it works, but I had the same problem. I believe I resolved it by running sudo aptitude purge firefox* followed by an rm -rf ~/.mozilla and manually searching for and destroying all references to Firefox. It's a messy and painful process, one that I avoid completely by not installing the Desktop distro (I install a CLI and use a script to build the environment around that).

---

