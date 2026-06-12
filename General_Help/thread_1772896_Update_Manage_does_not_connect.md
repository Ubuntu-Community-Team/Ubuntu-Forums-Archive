---
title: "Update Manage does not connect"
date: 2011-06-01
forum: General Help
---

### Post by David Crockett on 2011-06-01
HI all.

I get the following errors with update manager:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


What am I supposed to do?  I am running Ubuntu 11.04, updated yesterday.

Cheers,
DC

---

### Post by Rubi1200 on 2011-06-01
Hi,
run these commands in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---

### Post by David Crockett on 2011-06-01
Thanks,

I worked wonderfully.

I am now a happy camper.

DC:)

---

### Post by Rubi1200 on 2011-06-01
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page so that other users can find a working solution for situations like this.

Thanks.

---

