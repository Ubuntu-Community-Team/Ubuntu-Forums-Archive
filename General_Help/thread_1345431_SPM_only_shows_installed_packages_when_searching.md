---
title: "SPM only shows installed packages when searching"
date: 2009-12-04
forum: General Help
---

### Post by pieguy on 2009-12-04
I reinstalled 8.10 on my laptop and it has that synaptic package manager only showing installed packages when you search problem.  I know there was help posts on this subject but I couldnt find it in a google search.

So I need to be able to search for "ALL" packages in the spm but only installed packages show during a search.

---

### Post by plucky on 2009-12-04
> **pieguy said:**
> I reinstalled 8.10 on my laptop and it has that synaptic package manager only showing installed packages when you search problem.  I know there was help posts on this subject but I couldnt find it in a google search.

So I need to be able to search for "ALL" packages in the spm but only installed packages show during a search.

**System > Administration > Software Sources** and make sure the "repositories" are ticked. If they are,open a terminal and post output of ```
sudo apt-get update
```


Good Luck

---

### Post by audiomick on 2009-12-04
At the risk of stating the obvious, you can tell the package manager to only show installed. It is not that simple, is it? I shouldn't think so, as it a bit obvious.

On the bottom left of the window is a button called "status". If that is selected, one of the options top left is "only installed"

---

### Post by pieguy on 2009-12-04
No the problem isnt that simple, alot of people(including me) had this problem years ago and people posted some terminal commands to fix it.  It turns out that they fixed it in a update, because I updated and its working like it should now.

And just to add more info since some people thing its a source issue, the packages that are NOT installed show up just fine in the spm when you DONT search, its only when you SEARCH that only installed packages are displayed.

---

