---
title: "amaroK"
date: 2006-03-18
forum: General Help
---

### Post by sprinkles on 2006-03-18
Sorry for 2 threads by me in a short space of time, but I have another question.

Will the version of AmaroK in the repositories be updated?

The version there is currently 1.3.1, but the AmaroK site has 1.3.8. This version also fixes the broken lyrics problem, but there is no Ubuntu package on their site.

---

### Post by engla on 2006-03-18
Normally, old releases don't get feature updates for packages [only urgent updates for serious bugs and security]. If you want new releases the backports project (found on this forum) can help you in some ways.

Looking at [packages.ubuntu.com]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amarok&searchon=names&subword=1&version=all&release=all"), backports have actually backported amarok 1.3.7 to breezy, so if you add their repository it should be very easy to update to that version.

If I'm allowed to guess they won't backport any later versions, at least not for some time. Looking at the above link you can see that dapper will have amarok 1.3.8

* [Getting started with backports]("http://ubuntuforums.org/showthread.php?t=40291") has more info

---

### Post by Adrian on 2006-03-18
Maybe you will find this thread interesting:
[http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)

---

### Post by Jucato on 2006-03-18
No need to compile to get amaroK 1.3.8.
It has been released for Kubuntu, so you just need to add the repository for it.

You can find the instructions here: [http://kubuntu.org/announcements/amarok-1.3.8.php](http://kubuntu.org/announcements/amarok-1.3.8.php)

---

### Post by sprinkles on 2006-03-19
Thanks a lot, that worked fine :D

---

