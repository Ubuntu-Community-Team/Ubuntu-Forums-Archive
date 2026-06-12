---
title: "Partial window only in firefox"
date: 2009-11-15
forum: General Help
---

### Post by tomsax on 2009-11-15
For some unknown reason i can't get the window in firefox to fully maximise.  Annoying as I can't see webpages in full.  Very frustrating.  I was going to remove and then reinstall it but install/remove seemed to advise against it.

Any ideas on what to do about it welcome.

Tom

---

### Post by fluffman86 on 2009-11-15
Start: can other windows maximize? If so, then keep reading.  If not, then I can't help.

(1).  Backup and re-create your firefox profile with the following command:
```
cd ~/.mozilla/firefox && mv *.default olddefault.backup
```
Now, when you re-open firefox it should create a new blank profile for you.  Hopefully this will fix your problem.

---

