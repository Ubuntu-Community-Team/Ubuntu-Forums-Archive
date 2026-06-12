---
title: "apt error"
date: 2011-05-28
forum: General Help
---

### Post by xodaQo on 2011-05-28
I have two problems.  The first is that webpages load intermittently, and I don't even know what the second error is about but here it is:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

It's a brand-new install, maybe an hour old.  I've only uncommented two of the sources lines in the /etc/apt/sources.list.

What gives?

---

### Post by Rubi1200 on 2011-05-29
Hi and welcome to the forums :-)

Try this in the terminal:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

