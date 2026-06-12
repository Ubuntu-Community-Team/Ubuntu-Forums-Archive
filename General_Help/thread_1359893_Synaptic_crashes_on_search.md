---
title: "Synaptic crashes on search"
date: 2009-12-20
forum: General Help
---

### Post by El_Calavera on 2009-12-20
Hello everyone,

My Synaptic crashes whenever I enter anything into the search field, stating the following:
> Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 683, in <module>
    (dbkind, dbpath) = open(index).readline().split()
ValueError: need more than 0 values to unpack
Segmentation faultI have tried reinstalling synaptic without any change.

Perhaps this is of interest:
Before this started to happen, I had a system crash during an installation procedure (in the "Language Support" programme). I solved the consequent problems by using "sudo aptitude -f install"

Can anyone help? Thanks!

---

### Post by El_Calavera on 2009-12-20
Duh, I just did something trivial I should have done in the first place:
> $ sudo apt-get purge apt-xapian-index
$ sudo apt-get install apt-xapian-indexProblem solved. I'd have done this earlier, had I known xapian was a package...

Well, hope it helps anyone!

---

### Post by GAMaus on 2010-01-15
I love You!

---

### Post by axyelp on 2010-10-29
me too!!!

---

### Post by xerxies on 2011-04-10
I have searched for three days, yet couldn't find this.  Had I known it was this simple I would have really felt dumb.

> **El_Calavera said:**
> Duh, I just did something trivial I should have done in the first place:
Problem solved. I'd have done this earlier, had I known xapian was a package...

Well, hope it helps anyone!

---

