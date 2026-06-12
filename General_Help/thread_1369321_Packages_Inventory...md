---
title: "Packages Inventory.."
date: 2009-12-31
forum: General Help
---

### Post by nconceicao on 2009-12-31
I want to start off by saying happy new year to everyone, now my main question..

I've beens tasked with getting a list of all software installed on 

Solaris OS and Ubuntu, what is the most efficient way?

Do I basically do a man on packages ? or is there a more effient way?

Thank You

---

### Post by dcstar on 2009-12-31
> **nconceicao said:**
> I want to start off by saying happy new year to everyone, now my main question..

I've beens tasked with getting a list of all software installed on 

Solaris OS and Ubuntu, what is the most efficient way?

Do I basically do a man on packages ? or is there a more effient way?

Thank You

Use Synaptic.

---

### Post by todak on 2009-12-31
This: ```
dpkg --get-selections > installed-software
``` will generate a text file in your home folder of every package installed on your system. (for debian-based systems, anyway). See [http://www.tech-recipes.com/rx/1107/solaris-list-installed-packages-with-pkginfo/](http://www.tech-recipes.com/rx/1107/solaris-list-installed-packages-with-pkginfo/) for info on how to do it in solaris.

---

### Post by nconceicao on 2009-12-31
Will that work for Solaris as well?

---

### Post by todak on 2009-12-31
> **nconceicao said:**
> Will that work for Solaris as well?

Click on the link in my previous post for the method to use on Solaris.

---

