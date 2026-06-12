---
title: "How do I install Lucid's new Light theme on Karmic?"
date: 2010-03-04
forum: General Help
---

### Post by wersdaluv on 2010-03-04
[Light theme]("https://launchpad.net/ubuntu/+source/light-themes") is now out and [folks here]("http://ubuntuforums.org/showthread.php?t=1420913") are discussing it. 

I tried installing the package from Launchpad but it can't satisfy the "ubuntu-mono" dependency. I heard that it's the icon theme, but it could also be *the* mono.

How do I install the Light theme on Karmic? :)

---

### Post by iBurger on 2010-03-06
[http://launchpadlibrarian.net/40195509/ubuntu-mono_0.0.6_all.deb](http://launchpadlibrarian.net/40195509/ubuntu-mono_0.0.6_all.deb)

I'm pretty sure its the 'mono' icon set. If you install this deb first it all should work. (link comes from same page)

---

### Post by psyke83 on 2010-03-06
As well as "ubuntu-mono", you also need to grab the latest gtk2-engines-murrine package. Without the newer murrine engine, the theme will probably work - but widgets will not be themed correctly (as the Lucid version exposes newer murrine engine optons). The Lucid version should work on Karmic.

[http://packages.ubuntu.com/lucid/gtk2-engines-murrine](http://packages.ubuntu.com/lucid/gtk2-engines-murrine)

---

