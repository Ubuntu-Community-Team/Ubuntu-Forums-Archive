---
title: "guitesseract unexpected results"
date: 2010-06-13
forum: General Help
---

### Post by CoolJohnB on 2010-06-13
I have been trying to use guitesseract.py as a GUI front end for tesseract.  The GUI works great, and convetrs .jpg files to tiff, it then says it has processed the page and output it as a txt file. Here is a sample of the output:                                   55*/15C009+\+-*·9*5$Z¤·-+-*-0 +-*-:::1+ ::¤‘0000:+r*¤-+.*1+**--:+:+::0+-·04¤+—0 -·+--0 :5::+21v 0-*5 5 5w+-*5:++*1*:+ 59’ 05 ¢++¤9*+-**150-*0000w 9*+.055+-*-0+-*w< :+wD.+0.+w9*9*0U’2

As you can see it is NOT what I wanted!  If anyone can tell me why this occurs and
how to fix it it would be much appreciated.

Thanks in adance.

---

### Post by silvagroup on 2010-06-16
I too am having problems with gui for tesseract. So I am not sure I can be of much help, but for others who can this would be of help:
What version Ubuntu are you using?
What version of tesseract are you using?

For my problem I am usisng 9.10 repo version of tesseract and I need to install gtk 2.20, I am running 9.10 and it has 2.18, not good for tesseract as it looks for gtk 2.20. And since gtk is the backbone on gnome I am thinking that it will not be as simple as update gtk?

I think 10.04 is using 2.20, but was really not interested inthat option until all the bugs with nvidia drivers are worked out.

Anopther solution would be if any one has a good way to do multiple file conversion using tersseract, cli is only one file, tried tesseract *.tif *.txt and it was not a pretty thing.
Thanks in advance.

---

