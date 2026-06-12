---
title: "How to Merge 50+ pdf files in ubuntu"
date: 2011-07-06
forum: General Help
---

### Post by samMD on 2011-07-06
So I found PDftk which seems promising Im also looking at the commands which are also very powerful..but I think its kinda of laborious to type all my 50+ pdf files in the command prompt I have the front end of pdftk I was wondering is there a program (I have Pdf sam and Pdf Shuffler) that will allow me to import unlim. number of files and then just jam it into one big PDF file?

Thanks

---

### Post by tgalati4 on 2011-07-06
apropos pdf

I'm thinking you would do something like:

pdftops *.pdf - >> One_really_large_postscript_file.ps

pstopdf One_really_large_postscript_file.ps

Keep a fire extinguisher handy.

---

### Post by samMD on 2011-07-07
apropos pdf? When I google it nothing relevant shows up is it a program for ubuntu?

---

### Post by Nibr on 2011-07-08
Maybe this helps: [http://www.bukisa.com/articles/518220_merge-pdf-files-for-free](http://www.bukisa.com/articles/518220_merge-pdf-files-for-free)

There are 3 different way explained how to do it under Ubuntu. I think the command line option is exactly what you want.

---

### Post by samMD on 2011-07-09
@nibr thanks will look into that!

---

