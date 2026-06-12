---
title: "Where to put group folders on a multiuser system"
date: 2011-11-14
forum: General Help
---

### Post by opitzs on 2011-11-14
Hi,

this may sound stupid, but if want to create folders, that all members of a group can access, where should I put it? I mean what would be the most consistent in a linux system?

The following possibilities come to mind:

[LIST]
[*]/group-dir
[*]/groups/group-dir
[*]/home/group-dir
[*]/home/groups/group-dir
[*]/var/group-dir
[*]/var/groups/group-dir
[/LIST]
I can use each of those, but which one would be most correct?


Thank you
Sven

---

### Post by Lars Noodén on 2011-11-15
I don't see any mention of groups in [hier](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html).  My guess is that it should be under /home somehow.

---

