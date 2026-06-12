---
title: "How do I stop apt-get from displaying changelogs with less?"
date: 2011-07-26
forum: General Help
---

### Post by msp3k on 2011-07-26
Hi gurus,

One of the minor changes to Ubuntu seems to be that apt wants to display changelogs using less, which requires user interaction before apt proceeds to install the update.  This is a kind of an annoyance when you're using a script to propagate updates to a whole slew of machines.  Is there a way to turn this off -- or even better, change apt's use of less to cat.  (I don't mind the changelogs being displayed b/c I log everything my scripts do.  I just want to avoid the need for user input for automation purposes.)

---

### Post by msp3k on 2011-07-26
D'oh.  I forgot that I had already asked this question and found a solution: --quiet.

---

