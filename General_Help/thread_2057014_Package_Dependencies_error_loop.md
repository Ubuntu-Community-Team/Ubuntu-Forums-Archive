---
title: "Package Dependencies error loop"
date: 2012-09-12
forum: General Help
---

### Post by Dieuran on 2012-09-12
Hey all,

Was trying to install something today and then got this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ooobasis3.4-images needs to be reinstalled, but I can't find an archive for it.

```When to check for dependencies, and got this:
```

[COLOR=Red]sudo dpkg --remove --force-remove-reinstreq ooobasis3.4-images[/COLOR]
dpkg: dependency problems prevent removal of ooobasis3.4-images: openoffice.org3 depends on ooobasis3.4-images.
dpkg: error processing ooobasis3.4-images (--remove): dependency problems - not removing
Errors were encountered while processing:
 ooobasis3.4-images

```Tried to purge OO.org3 because I don't need it:
```
[COLOR=Red]sudo apt-get purge openoffice.org3[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ooobasis3.4-images needs to be reinstalled, but I can't find an archive for it.

```And we're back to square one. When to package manager, and got this:
```
E: The package ooobasis3.4-images needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```Searched around a bit and tried different solutions like:
```
[COLOR=Red]sudo dpkg --remove --force-remove-reinstreq openoffice.org3[/COLOR]
dpkg: dependency problems prevent removal of openoffice.org3:
 openoffice.org3-impress depends on openoffice.org3.
 openoffice.org3-writer depends on openoffice.org3.
 openoffice.org3-draw depends on openoffice.org3.
 openoffice.org3-en-us depends on openoffice.org3.
 openoffice.org3-base depends on openoffice.org3.
 openoffice.org3-math depends on openoffice.org3.
 openoffice.org3-calc depends on openoffice.org3.
dpkg: error processing openoffice.org3 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 openoffice.org3
```but obviously got errors.

/any ideas?

---

### Post by snowpine on 2012-09-12
Welcome to the forums!

OpenOffice is now LibreOffice, which is preinstalled in Ubuntu by default, so I'm not sure what is the problem exactly?

---

### Post by opensshd on 2012-09-12
try this:

sudo dpkg --remove --force-depends --force-remove-reinstreq openoffice.org3

---

### Post by Dieuran on 2012-09-12
> **snowpine said:**
> Welcome to the forums!

OpenOffice is now LibreOffice, which is preinstalled in Ubuntu by default, so I'm not sure what is the problem exactly?

 ooobasis3.4-images is missing. I can't ignore it, and when I tried to purge ooo it requires that ooobasis3.4-images problem be fixed.

I'm using Ubuntu 10.04 sorry I should have mentioned that before. So I had open office install on here.

---

### Post by Dieuran on 2012-09-12
> **opensshd said:**
> try this:

sudo dpkg --remove --force-depends --force-remove-reinstreq openoffice.org3

That worked perfect! Thank you!

---

### Post by opensshd on 2012-09-12
Cool! Please mark as solved in thread tools menu :)

---

