---
title: "sources.list regeneration"
date: 2011-09-23
forum: General Help
---

### Post by wbrb on 2011-09-23
A question for anybody who understands this particular design choice better than I do.

The sources.list file is generated or copied when an installation of ubuntu occurs. I've now read 20+ posts consisting of "make sure to backup sources.list" or "cp /etc/apt/sources.list ~/sources.list.backup" and whatnot.

For the people desperately googling there are websites that regen these lists but that don't pass GPG muster.

My main question is: **If the install CD can produce a sources.list file once, why never again? **

Or is there a way using a non-live CD to rebuild or extract a sources.list file that my searching has missed? Is there an official place to download one? Are there technical constraints here that make this a herculean effort that aren't apparent?

If somebody could direct me to some supplementary documentation about this design decision I'd be grateful.

---

### Post by patryk77 on 2011-09-23
One of my friends ended up with a corrupt list; it was very easily fixed.

I had him rename the sources.list file, go into System / Administration / Software Sources, check the needed options and reload.

The official software sources are simple to regenerate, but you might have to add any other sources you were using (Launchpad / VirtualBox, etc.)

---

### Post by seawolf167 on 2011-09-23
It is very easy to regen the sources.list file take a look [here ]("http://debgen.simplylinux.ch/")for example (Ubuntu version [here]("http://repogen.simplylinux.ch/")). The only issue you will run into is addition custom entries (PPAs, etc.), as unless you remember what you added, a new/default list won't have these entries until you manually add them again.

---

