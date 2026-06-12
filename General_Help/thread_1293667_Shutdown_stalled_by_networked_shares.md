---
title: "Shutdown stalled by networked shares"
date: 2009-10-17
forum: General Help
---

### Post by schwim on 2009-10-17
Hi there everyone,

Thanks to everyone's help on this forum, I've got a shiny new install of 9.10 on my work machine doing everything I need it to do.  It's truly smile inducing.  I have one little problem that's tugging at the edges of my smile though.

Let me just say that it's not Ubu specific.  For some reason, linux developers have yet to change the order of the services that are shutdown and network often gets shutdown prior to unmounting the networked drives.  This causes a one minute lag on shutdown.

I've looked online and found some threads both for other distros and for older versions of Ubu concerning dirty workarounds and bandaids, but I was wondering if there's anything specific for Ubu 9(.10) that I can do to resolve this issue?  A shell script that gets run at the beginning of the shutdown process or an alteration to the order would be totally awesome.

Thanks in advance for everyone's help.
json

---

### Post by schwim on 2009-10-18
Not a single person with an idea?

---

### Post by schwim on 2009-10-20
Thanks so much for all your help.

---

### Post by sdpiowa on 2009-10-20
I've never experienced this issue.  What causes the problem?

---

### Post by schwim on 2009-10-20
If what I've read is to be believed, linux developers(not just Ubuntu) have yet to fix a bug in which network shuts down prior to unmounting the network shares, causing shutdown to hang.

---

