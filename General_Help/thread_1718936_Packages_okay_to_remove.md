---
title: "Packages okay to remove ?"
date: 2011-04-01
forum: General Help
---

### Post by snoopy-2009 on 2011-04-01
i couldnt seem to find any threads of this nature, most just explaining HOW TO remove packages... Derrrr. lol.. anyway..

i was wondering which packages may be un-useful to some, and completely safe to remove from the original distro (10.10 anyway) 

im just working on making a "current state" list for dpkg, for future installs, i just wanted to add and remove packages needed/unneeded, and land at a solid state for my machine, before doing so.

---

### Post by Rubi1200 on 2011-04-02
One way of doing this would be to go to Synaptic and search for various packages, for example under Sections.

I think that what you decide to keep or remove is really a personal choice.

For example, I usually remove most games on a fresh install since I rarely, if ever, play them.

**Before removing anything, check the dependencies**.

You can also make a list of all installed packages:
```
dpkg --get-selections > installed-software
```

---

### Post by snoopy-2009 on 2011-04-07
thanks for the feedback!

---

### Post by Cheesehead on 2011-04-07
Apt has a couple nifty tools for this.

Apt tracks which packages you chose to add ('manual') vs. which packages simply get pulled in as dependencies ('auto'). Each package you have installed is marked with one of those.

The commands 'apt-get markauto' and 'apt-get unmarkauto' toggle that setting.

When you install from the LiveCD or AlternateCD, *all* the packages are marked 'manual', which reduces the usefulness of the setting. But it's easy enough to set the 'ubuntu-minimal', 'ubuntu-standard', and 'gnome/kde/xfce-desktop' packages as manual, and change the rest to auto.

Then, all you *really* need is the list of manually-installed packages.


Apt-get also has autoremove, to remove orphaned packages. Very convenient.

---

