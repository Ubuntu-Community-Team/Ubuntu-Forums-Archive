---
title: "Testing a Linux System"
date: 2011-10-24
forum: General Help
---

### Post by Jonny87 on 2011-10-24
Does anyone know of any scripts or lists of command that could possibly test any part of a Linux system that can be tested then give some sort of easy to understand report?

I know people that often complain that there is something wrong with their system but they cant seem to tell me what it is or when I'm looking at it I don't see anything wrong. I wan't something that can test anything and everything that can be tested from hardware issues to software issues, Graphics related stuff and security. Something that can at least show me where to start or highlight any underling problems that would other wise go undetected.

Perhaps there are some experts that could put something like this together. Any help would be appreciated.

---

### Post by c0nv1ct on 2011-10-24
You want some one-click universal diagnosis tool which really isn't going to work well in an environment like Linux.  Things are far too dynamic for that to be feasible.  Linux is so customizable that there really wouldn't be a metric to test anything against, at least on a universal and system-wide scale.  You might be able to come up with tools to test very specific things, like a functional toolchain for example, but a system-wide test would be impossible.

Linux is great about logging things.  Usually when there is a problem it is documented somewhere in /var/log or ~/.xsession-errors.  Learning to parse logs is the primary skill for troubleshooting Linux.  You may want to look into this for your troubleshooting woes instead.

---

