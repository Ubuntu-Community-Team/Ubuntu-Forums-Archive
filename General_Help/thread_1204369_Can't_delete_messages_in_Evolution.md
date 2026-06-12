---
title: "Can't delete messages in Evolution"
date: 2009-07-04
forum: General Help
---

### Post by nab on 2009-07-04
I have a mail message in drafts. When I go to File->Empty Trash, nothing happens. When I press CTRL-E, I get the error: Summary and folder mismatch, even after a sync

Just to remember the solution: 

To remove the error I found the solution in [http://forum.ubuntuusers.de/topic/evolution-loescht-muell-nicht-mehr/?highlight=evolution+mull+leer#post-1787924]("http://forum.ubuntuusers.de/topic/evolution-loescht-muell-nicht-mehr/?highlight=evolution+mull+leer#post-1787924")

shutdown Evolution in terminal:
evolution --force-shutdown

Delete the files Drafts*.* in folder ~/.evolution/mail/local (If you want keep the mail in the folder then keep the file Drafts)

If that's not working, delete after shutdown of evolution additionally to above files folders.db in folder ~/.evolution/mail/local
(With this step you loose the meta data in evolution)

---

