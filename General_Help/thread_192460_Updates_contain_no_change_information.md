---
title: "Updates contain no change information?"
date: 2006-06-08
forum: General Help
---

### Post by BaffledMollusc on 2006-06-08
Does anyone know why when we install updates now there is never anything in the "Change" field? I'd like to know why I should install a particular update, rather than just doing it blindly.

Is there some setting I have to change or something?

---

### Post by | MM | on 2006-06-08
im the same. any thoughts

---

### Post by BaffledMollusc on 2006-06-09
No one has any idea?

---

### Post by mlind on 2006-06-09
Changelog usually appears few hours after update has been released, dunno why.
You can see changes also on [https://lists.ubuntu.com/archives/dapper-changes/](https://lists.ubuntu.com/archives/dapper-changes/)

or use
```

aptitude changelog *package*

```

---

### Post by BaffledMollusc on 2006-06-09
[QUOTE=mlind]Changelog usually appears few hours after update has been released, dunno why.
You can see changes also on [https://lists.ubuntu.com/archives/dapper-changes/](https://lists.ubuntu.com/archives/dapper-changes/)

or use
```

aptitude changelog *package*

```[/QUOTE]
Great, thanks!

---

### Post by megahertza on 2006-06-09
I get a segmentation fualt when enter the following into the terminal

aptitude changelog package

---

### Post by mlind on 2006-06-09
[QUOTE=megahertza]I get a segmentation fualt when enter the following into the terminal

aptitude changelog package[/QUOTE]

you must replace package with package name, like
aptitude changelog **festival**

Nevertheless, aptitude shouldn't segfault..

---

### Post by nocturn on 2006-06-09
You don't have to change anything.  But I think the problem is that the devs are not supplying changelogs at this moment, I don't know why.

---

### Post by barthel on 2006-06-09
I've filed a bug report on this: [https://launchpad.net/products/update-manager/+bug/49147]("https://launchpad.net/products/update-manager/+bug/49147") since I'm able to download changelogs via Synaptic (Package -> Download Changelog) and the **aptitude changelog *package*** shell command.

It may well be a display issue, since the "check back later" message isn't appearing either.

---

