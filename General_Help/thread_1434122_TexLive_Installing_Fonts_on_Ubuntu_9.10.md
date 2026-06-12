---
title: "TexLive: Installing Fonts on Ubuntu 9.10"
date: 2010-03-19
forum: General Help
---

### Post by ashishjain on 2010-03-19
Dear All,

I have been trying to install the math font kurier for about two weeks now on a 32 bit Ubuntu (9.10) TexLive installation. The following are the steps I followed:-


[LIST=1]
[*]Copied all the contents of package kurier in the appropriate directories in $HOME/texmf
[*]Ran mktexlsr $HOME/texmf
[*]Created a file called '99local-kurier.cfg' in $HOME/.texmf-config/updmap.d
[*]The contents of this file are [ ';' stands for end of line] : "Map kurier-cs.map;Map kurier-greek.map;Map kurier-sy.map;Map kurier-texnansi.map;Map kurier-ec.map;Map kurier.map;Map kurier-t2a.map;Map kurier-ts1.map;Map kurier-el.map;Map kurier-mi.map;Map kurier-t2b.map;Map kurier-wncy.map;Map kurier-ex.map;Map kurier-qx.map;Map kurier-t2c.map;Map kurier-exp.map;Map kurier-rm.map;Map kurier-t5.map;"
[*]When all this did not work, I copied all the contents of $HOME/texmf to /usr/local/share/texmf
[*]Ran sudo mktexlsr
[*]Copied the cfg file to /etc/texmf/updmap.d directory
[*]Ran sudo update-updmap
[*]Ran sudo updmap-sys
[/LIST]
Now, when I try to compile the following simple tex file using pdftex, I get the warning "pdfTeX warning: /usr/bin/pdflatex (file qx-kurierr): Font qx-kurierr at 600 not found." Furthermore, when I try view the pdf, the pdf viewer shows a completely white blank file.
 
\documentclass[a4paper,10pt]{article}
\usepackage{kurier}
\begin{document}
This is just a test.
\end{document}

When I try to compile the same file using latex, it gives zero errors and warnings but when I try to view the dvi file, I can only see a bunch of small rectangular pixels in place of the text.
 
Kindly help.

Sincerely yours,
[COLOR=#888888]
Ashish[/COLOR]

---

### Post by ashishjain on 2010-03-25
My problem was resolved by a very knowledgeable person (in LaTex) from River Valley Technologies. 

If you ever read this, thank you again sir.

---

### Post by SnickerSnack on 2010-03-26
Maybe you can tell us what the solution is?.....

---

