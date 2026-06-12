---
title: "Real UID vs Effective UID ... how to create files as Effective UID"
date: 2011-08-10
forum: General Help
---

### Post by couling on 2011-08-10
Hi All

I've been experementing with getting sudo to leave the Real UID unchanged for some commands.  This is really helpful where those commands are logging who's doing what.

I'm having a problem though with the fact that when a program creates a new file it is created as the real user UID not the effective UID.  This means that if it closes the file handle to the file it actually looses the file permissions to open its own file!

Is there any way to change the default file creation to the Effective UID?  Or are there any other workarounds for this?

Regards

---

