---
title: "upgrading"
date: 2011-01-10
forum: General Help
---

### Post by robotz421 on 2011-01-10
I have Ubuntu 7.04 installed on my machine (i386) and I want to upgrade to Ubuntu 10.10 without going through all the intervening versions.  Is this possible and how would I go about it safely?  I don't currently have an internet connection because it is not configured (one of the reasons for upgrading.)  Any help would be greatly appreciated.

---

### Post by mcduck on 2011-01-10
Sorry, but no, it's not possible.

You can only upgrade from a release to the next release, or from an LTS release to next LTS release.

What makes things even harder is that the support for 7.04 ended in October 2008 and it's software repositories are already closed. And so are repositories for the next version, 7.10.

You could, in theory, handle the upgrade by changing your sources.list to point to old-releases.ubuntu.com, and then go trough a bunch of upgrades:
7.04 -> 7.10 -> 8.04 LTS -> 10.04 LTS -> 10.10
(and even that wold be a true pain if you don't have Internet connection on the machine)

..but really just getting the 10.10 install CD and doing a fresh install with it would take a lot less time and work to do. And it would be more likely to actually work without any problems... :)

---

