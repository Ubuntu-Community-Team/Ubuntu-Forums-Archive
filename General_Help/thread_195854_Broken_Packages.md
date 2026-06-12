---
title: "Broken Packages"
date: 2006-06-13
forum: General Help
---

### Post by cssutto on 2006-06-13
When I upgraded to dapper, it did not load the help file for Open Office.

So this morning, I need help.

I use package manager to install oo help and get the message that it cannot because of broken packages.

When I tell it to fix the packages, this is what I get:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

So I exit package manager, then load it again and ask for it to fix brocken pacages and it tells me that it has fixed them.

Then I ask package manager to install Oo Open Office.org2-help-en-us and get the same can't do because of brocken pacages.

I am in a loop.

This package removes all Oo packages and reinstalls a replacement.

Do I really want to do this and if so how?

By the way, the way I go into this is that I print multi-page docs and I get tired of sorting the pages in reverse.

I would like them to be printed in reverse so that page one is on top.

CSSJR

---

### Post by cssutto on 2006-06-13
False alarm.

I looked at my sources file and found that something changed everything back to breezy.

No wonder.

I used Automatix to resolve some of my DVD problems and that is what changed the sources file.

Luckily the back up file was still there.

A warning to anyone that uses Automatix.

CSSJR

---

