---
title: "How complete translations with gettext?"
date: 2009-06-29
forum: General Help
---

### Post by gaiterin on 2009-06-29
Hi!
Can I do this with gettext?

I have 2 files:
**1.po**:
[INDENT]msgid "Edit"
msgstr ""

msgid "File"
msgstr ""[/INDENT]


**2.po**
[INDENT]msgid "File"
msgstr "Fichero"

msgid "Width"
msgstr "Ancho"[/INDENT]

I like create a new copy of file 1.po, with ONLY translated strings of 2.po, then the final file must be this:

**final.po**
[INDENT]msgid "Edit"
msgstr ""

msgid "File"
msgstr "Fichero"[/INDENT]


Can be it possible?
I read this:
[http://www.gnu.org/software/gettext/manual/gettext.html](http://www.gnu.org/software/gettext/manual/gettext.html)
[http://www.faqs.org/docs/linux_scratch/appendixa/gettext.html](http://www.faqs.org/docs/linux_scratch/appendixa/gettext.html)
But I can't do it :(

Thanks very much!! :D

---

### Post by gaiterin on 2009-06-29
Uhm, I think with this:
Install translate-toolkit package, and in terminal run:
pomerge -t 1.po -i 2.po -o final.po
It works :D

---

