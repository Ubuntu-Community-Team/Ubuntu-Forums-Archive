---
title: "OpenOffice Writer: dragging on Ruler items not snapping to a grid"
date: 2010-02-04
forum: General Help
---

### Post by chewearn on 2010-02-04
In OpenOffice Writer, dragging on a Ruler item does not snap to a grid.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145958&stc=1&d=1265277712[/IMG]

E.g. I want to drag the "Indentation handle" by 1.00cm exactly.  But it does not snap to a grid.  So when I drag it, I got maybe 1.03cm or 0.98cm.

How do I set it so the Ruler conform to a coarse grid of say 0.5cm?  Then, I am assured when dragging, it will only land on 0.5cm, 1.0cm, 1.5cm, and so on.  And it would not be land on 0.79cm, 1.07cm, 1.43cm, etc.

---

Thank you for your kind assistance.

---

### Post by niteshifter on 2010-02-04
Hi,

With the cursor on the area of text you wish to change, double click on the gray areas of the ruler. This will bring up the Paragraphs dialog, displaying tab "Indents and Spacing". There you can precisely set your indent distances. 

I believe the ruler is non-gridded by design.

---

### Post by chewearn on 2010-02-04
> **niteshifter said:**
> Hi,

With the cursor on the area of text you wish to change, double click on the gray areas of the ruler. This will bring up the Paragraphs dialog, displaying tab "Indents and Spacing". There you can precisely set your indent distances. 

Thanks for pointing that out.  I am already aware I could do that, but it's annoying trying to customise a more than a few indentations this way.

Especially when I tried to precisely position blocks of text, due to a fault in the way my printer prints (that's another story).


> I believe the ruler is non-gridded by design.

Well, that's too bad.  Not a good design IMHO.  No way to fix it then?

---

### Post by niteshifter on 2010-02-04
Hi,

If you're going to do a lot of custom formatting, create custom styles and save them in a template document. F11 will bring up the Styles and Formatting chooser dialog - a very handy feature.

Keywords in OOo help: "styles" and "templates".

---

### Post by chewearn on 2010-02-05
Thanks for the suggestion.

The amount of custom indentations, or tabs, etc are not that many, such that it is worth the hassle of setting up custom styles.

For instance, if I write a letter, I would need one indentation setting for the address block.  Then, when I want to print the envelope, I would need four indentation settings.  I wrote a letter once every few months.

Not enough to worth setting up custom styles.  But just enough to make it annoying because I have to double-click on the ruler more than 10 times, to get the indentation just right.

Yes, I know.  I have a slight obsession with things being just right.  1.00cm perfect. 1.01cm I just can't leave it alone.

---

### Post by chewearn on 2010-02-05
Alright, found the bug report for this:
[http://www.openoffice.org/issues/show_bug.cgi?id=24070](http://www.openoffice.org/issues/show_bug.cgi?id=24070)

Bug has been open since 2004.  :shock:

---

