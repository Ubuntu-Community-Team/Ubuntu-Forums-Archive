---
title: "Help with SARG"
date: 2006-05-14
forum: General Help
---

### Post by msibleyj on 2006-05-14
I successfully installed sarg, but need some help in configuring it.  It needs a cron job, right?  What script would I use?

Mark

---

### Post by Divan Santana on 2007-02-02
Did you come right with this??

---

### Post by Divan Santana on 2007-02-02
Think I found the problem with sarg.

If you look at the cron jobs /etc/cron.daily
You will see if you run it manually it fails with a syntax error because the scripts point to /bin/sh which links to dash.

If you edit the sarg scripts to point to /bin/bash instead all should work

---

### Post by Divan Santana on 2007-04-18
Still haven't come right with SARG :( Anyone have any luck? Someone must have got SARG Squid reports working????

---

