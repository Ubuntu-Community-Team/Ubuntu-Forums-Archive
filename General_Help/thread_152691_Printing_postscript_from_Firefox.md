---
title: "Printing postscript from Firefox"
date: 2006-03-30
forum: General Help
---

### Post by chettyk on 2006-03-30
When I use the option in Firefox to print the web page as a file, I get a good reproduction of the page in the form of a postscript file. But when I use ps2pdf to convert the PS file to PDF, the resulting PDF has the images but not the text. 

The same thing happened when I installed and used cups-pdf to produce PDF files from within Firefox.

I then tested the same web page ([http://news.bbc.co.uk/text_only.stm](http://news.bbc.co.uk/text_only.stm)) with Knoppix 4.02. Both the PS file and the subsequent PDF file created by ps2pdf in Knoppix correctly reproduced the web page.

More surprisingly, when I transferred the PS file created in Knoppix into Ubuntu and then ran ps2pdf, the PDF file had both the images and the text.

Is there some issue with postscript printing from Firefox in Ubuntu or what?

---

### Post by SteveF on 2006-04-03
I have the same problem.  What I learned (after reading many forum posts) is that the output from Firefox has some incompatibility wiht the pdf viewers supplied with Ubunut (I've tried a few).  But, the resulting pdf file (using either cups-pdf or ps2pdf) is viewable by Adobe Acrobat.  So either there is some non-compliant part of PDF that Acrobat allows (and Firefox uses) or the pdf viewers supplied don't support everything correctly.

If using Firefox for your PDf output, I recommned installing Acrobat Reader.  I know there's a how-to on installing it.  It is in one of the repositories you need to add (I've added a few which is why I can't tell you exactly which one).  But I searched on acroread and installed.  Running acroread to open the pdf works fine.

Steve

---

### Post by chettyk on 2006-04-18
Sorry, Steve. I saw your message only today. 

Good grief! You are absolutely right. I just printed out this page using cups-pdf and I could open the PDF it produced without a problem in Acrobat Reader (which I already had on my system). But Evince 0.4.0, the default program for reading PDF files, could not produce a readable output with the very same PDF file. That's really strange.

Thanks so much for your help.

---

