---
title: "Lucid-System&gt;Help&gt;Advanced: ASCII gibberish in text -A bug?"
date: 2010-05-21
forum: General Help
---

### Post by emarkay on 2010-05-21
See Screencap.

System>Help and Support>Advanced Topics>Terminal Commands References (Man Pages).

I am sure it's just a simple codepage setting, but this is a recent  complete re-install, and I haven't  messed with that.

Can someone verify this and let me know and I can then file a Launchpad bug?

Thanks!

---

### Post by dcstar on 2010-05-22
> **emarkay said:**
> See Screencap.

System>Help and Support>Advanced Topics>Terminal Commands References (Man Pages).

I am sure it's just a simple codepage setting, but this is a recent  complete re-install, and I haven't  messed with that.

Can someone verify this and let me know and I can then file a Launchpad bug?

Thanks!

Works fine on my system.

Check the system locale and install any missing language files.

---

### Post by lisati on 2010-05-22
Confirmed: I get the same effect when I click on "Advanced Topics" then "Terminal Command References". The other pages I've checked display normally.

---

### Post by lisati on 2010-05-22
[QUOTE=emarkay]I always hate to do new bug reports when the package it's part of is not obvious.

Any hints on how to find the package ; other than a lucky hit on a Google search?

Thanks!

MRK[/QUOTE] 
Now to figure out a bug report.
On my machine the relevant file is
file:///usr/share/gnome/help/advanced-topics/C/advanced-topics.xml
and the unintelligible stuff appears when I click on a link: ghelp:basic-commands

Clicking on a few links in the help files took me to the help wiki @ [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

I'm about to take a break from my computer.

---

