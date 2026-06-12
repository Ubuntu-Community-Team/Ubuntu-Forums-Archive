---
title: "Packages that depend on the given one"
date: 2012-04-25
forum: General Help
---

### Post by swarog on 2012-04-25
Hi all,

How can I get a list of all packages in the repository in use that depend on a given one?

---

### Post by techsupport on 2012-04-25
> **swarog said:**
> Hi all,

How can I get a list of all packages in the repository in use that depend on a given one?

I install synaptic package manager.

Search for whatever package you want to learn about the dependencies of.

```
sudo apt-get install synaptic
gksu synaptic
```

:guitar:

---

### Post by strask on 2012-04-25
Maybe try ```
apt-cache showpkg *package-name*
```
Look at the "Reverse depends" section of the output.

---

### Post by techsupport on 2012-04-25
> **strask said:**
> Maybe try ```
apt-cache showpkg *package-name*
```Look at the "Reverse depends" section of the output.

That works better. I forget about that one.  Good job! 

:lolflag:

---

### Post by gordintoronto on 2012-04-25
Another option is to go to packages.ubuntu.com, select your version, find the package. It will show the "depends."

---

