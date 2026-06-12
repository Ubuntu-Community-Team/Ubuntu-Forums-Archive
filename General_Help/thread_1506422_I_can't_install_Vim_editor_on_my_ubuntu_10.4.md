---
title: "I can't install Vim editor on my ubuntu 10.4"
date: 2010-06-10
forum: General Help
---

### Post by arunkrishnan on 2010-06-10
Tried      sudo apt-get install vim-full

Got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vim-full



applied sudo apt-get update
still I can't install the vim editor

---

### Post by RiceMonster on 2010-06-10
I believe you can just install the package "vim" rather than "vim-full" and it should be fine.

---

### Post by arunkrishnan on 2010-06-10
still the result is negative

Unable to fetch some archieves

---

### Post by gmargo on 2010-06-10
There are multiple variations of vim packages that you could install.  Assuming you are using gnome, your best bet is to install the **vim-gnome** package.

[http://packages.ubuntu.com/lucid/vim-gnome](http://packages.ubuntu.com/lucid/vim-gnome)

---

### Post by ba_saish on 2010-06-11
see if you have included the default repositories. Then reload or apt-get update and then try again.

---

### Post by arunkrishnan on 2010-06-11
default repositories???
How can I add that?

---

### Post by Emmtor on 2010-08-28
On your screen:
System>Administration>Software Sources
The first two tabs refer to repositories.
Check the boxes that are unchecked, and try again.

---

