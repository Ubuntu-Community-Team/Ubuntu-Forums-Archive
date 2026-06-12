---
title: "Cannot read LaTex document"
date: 2010-05-31
forum: General Help
---

### Post by triplemaya on 2010-05-31
Hi. I'm trying to read this document.

[http://philsci-archive.pitt.edu/archive/00001053/01/Barrett-1.txt](http://philsci-archive.pitt.edu/archive/00001053/01/Barrett-1.txt)

which is on the page at 

[http://philsci-archive.pitt.edu/archive/00001053/](http://philsci-archive.pitt.edu/archive/00001053/)

I have installed texlive-full, and Winefish LaTex editor. The document opens, but the formulae are not interpreted. The app does not even seem to interpret any of the meta text, comimg out as: 



\documentstyle [12pt]{article}



\begin{document}



\title{Are Our Best Physical Theories \\ (Probably and/or Approximately) True?}



\author{Jeffrey A. Barrett}



\date{15 January 2003}



\maketitle





\begin{abstract}

Winefish will only show the document if I rename it to  ...tex. If I open it as it is saved on the hard drive the document is blank.

I'm using gnome in karmic.

Please could someone enlighten me as to how to read this document.
Thanks in advance.

---

### Post by davidmohammed on 2010-05-31
never used latex myself, but this [thread]("http://ubuntuforums.org/showthread.php?t=8427") (while a little old) may help...

---

### Post by Zemblan on 2010-05-31
Latex is a markup language for typesetting, but it does not work like html. It needs to be processed through latex which will output a pdf or a dvi file which you can read. 

Save the document, then open a terminal and run the command

```
latex mydocument.tex
```

It will process it and output a dvi file which you should be able to read with evince etc. 

Alternatively, you could Lyx, which while not wysiwyg per se, will display the document in a more readable format, and allow you to output to various file formats like pdf.

---

### Post by triplemaya on 2010-05-31
Many thanks for that. kile works a treat.

At first I thought none of that makes a difference.

As suggested on that link I've now installed 
tetex-base
tetex-bin
tetex-extra
texlive
texmaker
and kile

and when I opened the document with kile all I saw was the text with metatext. But when I pressed the pdf button, bingo! A perfect pdf document was created.

Still can't get any joy from winefish though. It opens the document with all the meta text, but there doesn't seem to be any way to view the text 'properly' or export to a readable form.

Anyway, problem solved by kile

Cheers

---

### Post by Zemblan on 2010-05-31
Glad you got it sorted. I suggested Lyx rather than Kile because kile is KDE, but similar thing.

---

### Post by triplemaya on 2010-05-31
Thanks for you help Zamblan. Now I get it!

In case it helps anyone, the latex works fine, but the kile produces a much better looking document.

---

