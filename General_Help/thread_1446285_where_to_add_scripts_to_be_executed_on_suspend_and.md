---
title: "where to add scripts to be executed on suspend and resume?"
date: 2010-04-03
forum: General Help
---

### Post by ant2ne on 2010-04-03
Suppose I need to run a script just before suspend. And another just after resume. Where would I put these scripts?

What about the same things for hibernate and wakeup?

Thanks!!

---

### Post by us3r on 2010-04-04
The folder you are looking for is /etc/pm/sleep.d/

Here's the only instructions I've found that describe how it works:

[http://en.opensuse.org/Pm-utils]("http://en.opensuse.org/Pm-utils")

---

