---
title: "Word documents won't load by click, only works by loading from within word"
date: 2010-03-17
forum: General Help
---

### Post by seemore on 2010-03-17
I am running Word2007 through wine and I cannot double-click on a document and have it open in word. Word will always tell me that it cannot be found. If I open the document from within word then it works.
Also, some docx files that are opened from within word just show a blank page.

ubuntu 9.10
wine 1.1.38
karmic koala
Word2007

Does anyone have any ideas on what could be causing this?

---

### Post by quixote on 2010-03-18
There's no file association for word under wine in gnome.  You can make one, but it'll be a bit of an Easter egg hunt to figure out exactly the right syntax.  The file you need to edit is:```
gksudo gedit /etc/gnome/defaults.list
```The entries in that file look like this: "application/vnd.ms-word=openoffice.org-writer.desktop".  That one associates .doc files with openoffice.  But what exactly you'd have to do for your more complicated situation, I'm not sure.  You could try searching for "mimetype docx wine Word" (all the words, but no quotes) and see if that gets you something?

(And, yes, there should be a much easier way to do this.  Maybe there is and I just don't know about it.)

---

### Post by seemore on 2010-03-19
Thank-you for the explanation about .doc attachments.

---

