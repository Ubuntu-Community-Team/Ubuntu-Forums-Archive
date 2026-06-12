---
title: "KILE+OKULAR (use ViewPDF to close old OKULAR windows))"
date: 2009-09-15
forum: General Help
---

### Post by Vari on 2009-09-15
[SIZE=1]Hi,

I'm producing a LATEX document using KILE and as the viewer I use OKULAR. What currently happening is that when a I do QuickBuild, or for that matter PDFLateX+ViewPDF, a window for OKULAR is opened. This is OK if you do it once. But after several QuickBuilds you'll end up with a huge pile of OKULAR windows for which  you no longer have any use. So, what I'm looking for its away to ViewPDF automaticaly close any old OKULAR windows that may be open before it loads the new document. [/SIZE]

Do you know how can I do this?

---

### Post by Vari on 2009-09-16
I presume that what I have to do is to input the right options  in Settings -> Configure Kile -> Tools -> Build -> ViewPDF. For command Okular, the default option is '%target' but there must be an option that allows me to open my pdf document without opening a new window. i.e., in case Okular already has an opened window this is the window to be used.

I hope this helps clarifying my question.

---

### Post by TerpInHotLanta on 2009-11-11
I found a solution in TexMaker that may apply to Kile. If you have the ability to change the command Kile uses to explicitly call Okular, use the --unique flag

Example in Texmaker:

PDFView Command: okular %.pdf

Changed to

PDFView Command: okular --unique %.pdf

Worked for me-- hope this helps!

---

### Post by P3t3r on 2010-05-02
Just wanted to update this: in the newest Kile you can just replace "okular" by "okular --unique" as command. :)

---

### Post by DadsArmy on 2012-01-18
Okular doesn't work for me, it doesn't show the file when I quickbuild. Evince does exactly what you want.

---

### Post by Elfy on 2012-01-18
Old thread closed.

---

