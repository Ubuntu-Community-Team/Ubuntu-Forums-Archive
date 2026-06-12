---
title: "chm2pdf processes only first 2 or 3 pages"
date: 2009-09-07
forum: General Help
---

### Post by bilol on 2009-09-07
Dear all,
The chm2pdf is not working properly.It is producing the first few pages of my chm document.How can I convert the **whole** .chm document to .pdf ? 
I use the command:
```
 chm2pdf --webpage   --color dataStr.chm 

```
Need your help.....

---

### Post by bilol on 2009-09-08
can anybody help me out of this problem??

---

### Post by yabbadabbadont on 2009-09-08
[http://code.google.com/p/chm2pdf/issues/list](http://code.google.com/p/chm2pdf/issues/list)

A couple of those open issues look like they might be related to yours.  You should look through them and see.  If none of them apply to you, try submitting a new issue.

---

### Post by bilol on 2009-09-08
Than you yabbadabbadont.
It was told there, that I have to edit the PageLister class to solve the problem. Where is this class located in ubuntu?

---

### Post by yabbadabbadont on 2009-09-08
In a terminal, use ```
dpkg -L chm2pdf
``` to see a list of all the files installed by the package.  Look for a python file (*.py) that is named something like what you are looking for.  I don't have this package installed, so I can't tell you exactly what and where.  You could always post a comment on that open issue asking for guidance.

---

### Post by bilol on 2009-09-09
Thanks a lot yabbadabbadont for your valuable suggestions.

Ultimately the problem get solved.
Anybody like me wanting to convert his huge .chm document to .pdf should follow the following steps:
(1) $ *sudo apt-get install chm2pdf* # to install the chm2pdf
(2) Let the .chm file is source.chm and it is placed in /home/urname/
(3) $ *chm2pdf --extract-only /home/urname/source.chm* # all extracted html files will be stored in /tmp/chm2pdf/orig/source/8157final
(4) $ *htmldoc* # to open the HTMLDOC window
(5)Click <Add Files> in HTMLDOC window  and browse to /tmp/chm2pdf/orig/source/8157final/ then  select all .html files and click <OK>
(6) click <Output> and select <pdf> radio button as Output Format ,then write the Output Path as  /home/urname/target.pdf and click <generate>
(7) The required .pdf will be found in /home/urname/target.pdf

---

