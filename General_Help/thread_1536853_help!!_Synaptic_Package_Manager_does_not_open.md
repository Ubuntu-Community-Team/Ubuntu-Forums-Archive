---
title: "help!! Synaptic Package Manager does not open"
date: 2010-07-22
forum: General Help
---

### Post by fino on 2010-07-22
i was installing sun java6 in Open Office to use with Zotero. I entered a list of commands in terminal (never again, from now on cut & paste!) that I got from here: [http://blog.martineve.com/running-zotero-on-ubuntu-lucid](http://blog.martineve.com/running-zotero-on-ubuntu-lucid) . I entered one of the commands incorrectly and now this pops up when i try to open Synaptic Package Manager:

E: Type 'debhttp://archive.canonical.com/ubuntu' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

can anyone explain to me how to fix this problem i created? thanks!

---

### Post by Nytram on 2010-07-22
There should be a space after the word **deb** in the following line:

**E: Type 'debhttp://archive.canonical.com/ubuntu' is not known on line 57 in source list /etc/apt/sources.list**

You can correct this manually by opening up a text editor and inserting the space on line 57 (most likely the last line) ie:

**gksu gedit /etc/apt/sources.list**

---

### Post by Drone4four on 2010-07-22
After changing your sources.list, don't forget to run sudo apt-get update.

---

### Post by fino on 2010-07-25
Thank you both!! I followed your directions and things seem to be a-okay again!

Fino

---

