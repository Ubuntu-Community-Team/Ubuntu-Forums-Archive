---
title: "Dependencies"
date: 2009-08-26
forum: General Help
---

### Post by Elep.Repu on 2009-08-26
Where would I look within the source folder (I'm compiling) for a list of dependencies? The site does not list them. Do I just have to manually install each one, as it comes to each required dependency error when I run ./configure?
This program is within the Intrepid and Hardy repositories but not the Jaunty.
I would prefer to compile it anyway, just because I started to.

I'm curious if what I am doing (./configure, oh I need that, ./configure, Oh I need *that*) is dumb..

---

### Post by dmonkey on 2009-08-26
The only way I know of is to use

sudo apt-get build-dep <package>

but this will obviously not work if your package is not in the repositories. You could try to temporarily add these repositories, but I'm not sure what the effects might be.

Alternatively, shout at the developers of the program until they tell you.

Incidentally, "./configure, oh I need that, ./configure, Oh I need that" is dumb, but that's the linux way!

---

### Post by Elep.Repu on 2009-08-26
> **dmonkey said:**
> The only way I know of is to use

sudo apt-get build-dep <package>

but this will obviously not work if your package is not in the repositories. You could try to temporarily add these repositories, but I'm not sure what the effects might be.

Alternatively, shout at the developers of the program until they tell you.

Incidentally, "./configure, oh I need that, ./configure, Oh I need that" is dumb, but that's the linux way!

Really?
I figure there would be a list of dependencies..

---

### Post by dmonkey on 2009-08-26
Not unless the developer was generous enough to include such information (some are). Otherwise the only way to know is if ./configure spits out errors.

---

