---
title: "package rj not available in StatET Eclips"
date: 2011-06-08
forum: General Help
---

### Post by nethero on 2011-06-08
Running Ubuntu 11.04, Eclipse 3.6, StatET 0.9.2, and R 2.12

I installed everything successfully with no error messages but I keep getting this everytime I try to set up an RJ console.  Anyone have any ideas what I should try next?  Here is the error...

```
[INFO] The R package 'rj' is not available, R-StatET tools cannot be initialized.
```

---

### Post by nethero on 2011-06-10
Solved it.  I opened a r console and typed...

```
("rj" %in% installed.packages()[,"Package"])
```it returned TRUE, so that meant that the rj package was installed properly.  I typed...
```

.libPaths()
```and saw that after installation of the rj package that a new library path had been added.  This library path was something like...  /usr/local/lib...R/   grrrr can't remember.  Anyway, I opened Eclipse and went to Windows->Preferences->StatET->R Environment->selected my R configuration and clicked edit and added this new library path to the libraries section.  I restarted Eclipse and the error message went away.  Everything seems to be working now.

---

