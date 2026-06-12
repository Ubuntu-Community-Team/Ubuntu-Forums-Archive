---
title: "Diff for OpenDocument Text documents (for subversion)"
date: 2006-03-28
forum: General Help
---

### Post by mygravity on 2006-03-28
Hi,

I'm interested in adding some OpenDocument Text documents to our Subversion repository, and being able to do a command line diff on the files.

The best I've found so far is a Visual Basic application that fires up Open Office in compare mode:
[http://http://www.oooforum.org/forum/viewtopic.phtml?t=2853]("http://http://www.oooforum.org/forum/viewtopic.phtml?t=2853")
However not ideal for Linux!

Does anyone know of such a command line tool?

TIA

Andrew

---

### Post by rmjokers on 2006-03-29
Not sure if you are aware of this, but the new OpenDocument format files are just zipped plaintext XML documents.  If you use the command line unzip tool, you can get access to the raw data and use regular text comparison tools such as diff.  Of course, the XML and other formatting stuff might mess up the diff algorithm, but it might be worth a try.

---

### Post by hoakz on 2006-04-02
Ummm... As was the old swx files.

However unzipping and comparing hardly suffice.  For one, you'd get XML instead of text, and it would neither be pretty XML nor easy to comprehend XML.  (At least relative to pure text diff).

Secondly, I for one feel that a versioning and diff tool for anything else than pure source code needs to be able to read a whole bunch of formats, and I mean both the diff tool and the versioning tool.  After all, if I change a letter in my OpenDocument text and subversion is unable to recognize the format, the whole document will be replaced on next check-in.

But, okay, I can live with that.  Drive space is cheap.  However, what use do I have for versioning if I have to check out versions I want to do diff on and compare them by hand?

---

### Post by jason.e.stewart on 2008-04-08
Hi,

These two projects support interaction with the subversion version control system, and thus give you a diff of open office documents. They may help.

[http://sourceforge.net/projects/ooosvn/](http://sourceforge.net/projects/ooosvn/)

[http://sourceforge.net/projects/odfsvn/](http://sourceforge.net/projects/odfsvn/)

Cheers, jas.

---

