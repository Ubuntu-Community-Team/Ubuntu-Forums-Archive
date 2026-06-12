---
title: "reading .doc and .docx"
date: 2009-07-04
forum: General Help
---

### Post by Laeys on 2009-07-04
I just installed Ubuntu 9.04 (I am dual-booting with windows xp).  I have a bunch of .doc and .docx files that I still need, but are not converting with openoffice 3.  Some of the files open fine but most have had the first two letters of the filename replaced with ~$ and when opened they just have a small paragraph of weird symbols.  How can I open these files?

---

### Post by FrogPrince on 2009-07-04
Have you tried with Openoffice 3.1. [Here]("http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html") are the instructions. If that doesn't work, you can try a  converter. [Here]("http://www.getdeb.net/release.php?id=1995")'s one.

---

### Post by DeMus on 2009-07-04
> **Laeys said:**
> I just installed Ubuntu 9.04 (I am dual-booting with windows xp).  I have a bunch of .doc and .docx files that I still need, but are not converting with openoffice 3.  Some of the files open fine but most have had the first two letters of the filename replaced with ~$ and when opened they just have a small paragraph of weird symbols.  How can I open these files?

The files which you can not open in OpenOffice.org do they contain "strange" fonts or special formatting, tables, macro's?
A normal written text file written in Word can be opened and edited fine with OOo. Special documents are still a problem, as it is with every conversion.
When a filename starts with ~$, doesn't that mean the file is in use? I just googled a bit, but can't find it there.
Maybe somebody else knows it.

---

### Post by Gizenshya on 2009-07-04
^^^ this has been my experience as well.

Normal documents work fine.  But macros almost always break.

there was one that was especially bad.  in a management simulation I just completed (capsim.com), the macros completely screwed everything up.  it was completely unrecognizable.  I think many (most? all?) macros end up calling for windows dll files or soemthing...

---

### Post by Wim Sturkenboom on 2009-07-04
Files with ~$ are temporary files that MS word creates when you edit a word document. I can not say anything about the content, but from your description they ain't word documents.

---

### Post by Laeys on 2009-07-04
Well I feel a little dumb, the files were indeed just temporary files or something and the actual documents were elsewhere and converted with no apparent problems. Thanks everyone for helping out anyway. 

As a side issue I don't know if 3.1 has any noticeable improvements but I was unable to upgrade, is that worth looking into?

---

### Post by akakingess on 2009-07-04
> **Gizenshya said:**
> ^^^ this has been my experience as well.

Normal documents work fine.  But macros almost always break.

there was one that was especially bad.  in a management simulation I just completed (capsim.com), the macros completely screwed everything up.  it was completely unrecognizable.  I think many (most? all?) macros end up calling for windows dll files or soemthing...

I know that I have converted excel files with macros that opened and worked fine in OOo just fine with absolutely no problems, but I have yet to figure out which types of macros do mess it up. So far all of mine have converted.

akakingess

---

### Post by jbeaunaux on 2010-04-07
Gizenshya, did you ever figure out how to get capsim to work with Ooo? Or did it just not work for you at all?

---

### Post by gadolinio on 2010-04-07
> **Wim Sturkenboom said:**
> Files with ~$ are temporary files that MS word creates when you edit a word document. I can not say anything about the content, but from your description they ain't word documents.

+1. When you open a .doc file, another file whose name starts with ~$ appears, and it goes away when you close the document. They're temporary files, i guess.

---

