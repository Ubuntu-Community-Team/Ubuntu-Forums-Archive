---
title: "How to bypass the OO.o Document Recovery"
date: 2009-10-08
forum: General Help
---

### Post by Heretrix on 2009-10-08
Is there anyway to bypass the Document Recovery after a crash using OO.o? It keeps attempting to recover an Untitled1 file. I tried:

*openoffice.org -norestore*

and it returns with:

*terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'*

I've also tried to reinstall the program, but this problem persists.

Anyone know another method to bypass the Document Recovery, that or fix the RuntimeException or whatever it is?

FYI, I'm running Jaunty.

---

### Post by jmszr on 2009-10-08
Heretrix,

This should work: Places > Home Folder > View > Show Hidden Files > .openoffice.org > 3 > user > registry > data > org > openoffice > Office > Recovery.xcu (delete the file "Recovery.xcu").

This will also reset settings for "Autosave" in the OO.o Tools > Options> Load/Save > General dialog. 

Adapted from:[http://www.oooforum.org/forum/viewtopic.phtml?t=65016](http://www.oooforum.org/forum/viewtopic.phtml?t=65016)

---

