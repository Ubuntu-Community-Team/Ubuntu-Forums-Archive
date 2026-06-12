---
title: "Error while installing/unninstalling software"
date: 2009-07-26
forum: General Help
---

### Post by Revender on 2009-07-26
I've been using Ubuntu for 2 weeks but this problem started bugging me.I looked on google but it didn't help me, checked if this problem was already posted here, but nothing.
Here's my problem: Everytime I install something i get this error: E: "netatalk: subprocess post-installation script returned error exit status 1".Good...I click Close then another error:
"Not all changes and updates succeeded.For further details of the failure, please expand the 'Details' panel below."
The details panel stops at : Errors encountered while processing: netatalk.

It seems that the programs installed work but I want to get rid of this error.

---

### Post by ptn107 on 2009-07-26
```
sudo aptitude purge netatalk
```

---

### Post by Revender on 2009-07-26
Wow...that was fast, thank you, it really worked.

About your signature, sorry for the off-topic..Please mark completed threads as [COLOR=Red]**[SOLVED]**[/COLOR], which lets us find solutions faster!

Is there a way for me to mark this thread as SOLVED?

---

### Post by ptn107 on 2009-07-26
At the top under 'thread tools' there used to be such an option.  They removed it for the time being.  Right now you can just add [SOLVED] to the title.

---

