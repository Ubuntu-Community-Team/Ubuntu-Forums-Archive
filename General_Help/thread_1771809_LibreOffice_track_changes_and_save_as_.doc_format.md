---
title: "LibreOffice track changes and save as .doc format"
date: 2011-05-30
forum: General Help
---

### Post by ianc1 on 2011-05-30
Hi all

I'm using LibreOffice 3.3.2 to open a document I received through work.  The document is from MS Word in .doc format and has some track changes.  I started using Libre Office to track my changes to the document but the only format I can save it in and retain my changes is .odt which is fine for me.  However I would like to return this in .doc format.

It seems odd that LibreOffice happily opens a document with track changes but cannot save them back in that format.

Am I doing something wrong?  I am using Edit>Changes>Record and then File>Save As.

Does anybody have any ideas.  Any help would be great as I really don't want to resort back to Word let alone do all the changes again in it.

Thanks

---

### Post by AlphaLexman on 2011-05-30
I am not on a machine with LibreOffice, but with OpenOffice, but the similarities are very close to date.

Goto and click 'File -> Versions -> Always save a version on closing'

Always save a copy in native *.odt format before exporting to *.doc format.

---

### Post by ianc1 on 2011-05-31
Thanks AlphaLexman.  I've now tried this on both my Ubuntu 11.04 machine and my netbook which is running Crunchbang.  Both with LibreOffice 3.3.2 and also 3.4 on the netbook.  This still seems to still be an issue for me.

Both machines allow me to enter the file name and choose the format.  I then get asked do I wish to keep this format.  On selecting yes the file starts to save and then LibreOffice crashes.

The Ubuntu machine leaves files with names along the line of .~lock.ORIGINAL-FILE-NAME.odt#.  These contain:```
Username ,username,pc name,31.05.2011 18:51,file:///home/username/.libreoffice/3;
```The Crunchbang version leaves files hs_err_pid####.log (####=numbers).  Which seem to be logs of java openJDK fatal errors.

---

### Post by CKP on 2011-06-22
I'm seeing the same behavior in LibreOffice 3.3.2.  I'm trying to save a document with changes tracked and it crashes for .doc, .docx, filetypes.  I'm considering deprecating LibreOffice (is that a bad idea?).  I will probably turn off the change tracking and see if I can just export MS Word format normally.

---

### Post by ianc1 on 2011-06-22
Hi CKP  I'm sorry to say that I have not yet found a solution.  For the document I was editing I had made too many edits to do the work in another package so I exported a PDF and sent that to my colleague.  At least then my changes could be seen, although the extra hassle for him was not appreciated.  What would you use instead if you chose an alternative?  I did find a Microsoft site (I think), which unfortunately I cannot relocate, which had a list of what bits of MS Office were compatible with alternatives and under Libre Office/Open Office track changes was listed as not fully compatible.  Please post back if you find a solution or work around for this/  Thanks

---

### Post by b3nny_mac on 2011-09-07
I am having the same problem...  A colleague of mine has given me a .doc document to edit, and I recorded the changes.  However, when I save the file to a .doc format the comments still appear, but my tracked changes are there but are not highlighted, underlined, crossed out etc.  Any thoughts how my colleague will be able to see my tracked changes in her word application?

much appreciated

---

### Post by DrKay on 2011-10-27
> **b3nny_mac said:**
> I am having the same problem...  A colleague of mine has given me a .doc document to edit, and I recorded the changes.  However, when I save the file to a .doc format the comments still appear, but my tracked changes are there but are not highlighted, underlined, crossed out etc.  Any thoughts how my colleague will be able to see my tracked changes in her word application?

much appreciated


I am having this identical issue. It seems that the track changes data that is recorded in the doc file is not compatible with Microsoft Word. I just filed Bug #882793 about this issue:

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/882793](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/882793)

---

### Post by mtn on 2012-02-07
I installed Ubuntu 11.04 on my mothers netbook and she is having the same problem as above i.e., when she makes changes to a .doc document and sends it to her colleges who open it with MS Office 2010, the tracked changes are not accessable.

Hss anyone got an idea how to get round this? Or when this will be fixed?

Thanks

---

