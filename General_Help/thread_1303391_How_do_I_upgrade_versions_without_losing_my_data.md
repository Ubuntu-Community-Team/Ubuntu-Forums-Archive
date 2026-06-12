---
title: "How do I upgrade versions without losing my data?"
date: 2009-10-28
forum: General Help
---

### Post by Vigh on 2009-10-28
Hi was just wondering if it was possible to upgrade from say 8.10 to 9.10 when it is released without losing my installed programs and data. Cheers Ant

---

### Post by Psycho.mario on 2009-10-28
When ubuntu 9.10 comes out, update manager will tell you, if you upgrade using update manager, all your files and settings should be preserved. Some settings may not be preserved if they do not apply to ubuntu 9.10

---

### Post by spiderbatdad on 2009-10-28
Multiple distribution upgrades is generally not preferred...this is what you're talking about because you would first upgrade to 9.04. It is supposed to be possible to upgrade LTS to next LTS. In any event no one can guarantee your data, so you must back up anything you arent willing to loose.

---

### Post by grizato on 2009-10-28
If you can afford it, try and do a clean install, I've heard that you dn't get the famous fast boot from Karmic unless you do one!;)

---

### Post by jmore9 on 2009-10-28
When i did my update i did not lose any of my files on the hard drive.  Nor did i lose any of the needed apps i run via wine.

I just did the following and used the recommended selections.

ALT + F2

update-manager -d

about 1 hour later i had 9.04 updated to 9.10

---

### Post by phillw on 2009-10-28
> **grizato said:**
> If you can afford it, try and do a clean install, I've heard that you dn't get the famous fast boot from Karmic unless you do one!;)

That'd be down to your existing files still being in ext3 format, even tho' ext4 is the default for koala, but it doesn't transfer over.

I'm also going to just do the upgrade to start with, then a system backup, reformat & re-install once I'm happy with everything.

And, yes - before you do anything major to your system - always do a backup !!

Regards,

Phill.

---

