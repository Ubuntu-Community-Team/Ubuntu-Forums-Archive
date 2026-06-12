---
title: "Kile and Acrobat Reader as default document viewer"
date: 2009-07-23
forum: General Help
---

### Post by gemm on 2009-07-23
Hello,

I am using Ubuntu 8.10 and the Latex editor Kile. The default PDF viewer in Kile was Okular, and I have change it to Acrobat Reader (acroread). When the default was Okular, I didn't need to close and then open the PDF document after each new conversion with PDFLaTeX, because the update of the already opened PDF file took place automatically. Now when I have made Acrobat Reader the default PDF viewer, every time I change something in the tex file, save the tex file, and then convert with PDFLaTeX, I need to first close the opened PDF file and then open it again, so that I can see the changes. Is it possible not to do this, but to make this automatically as it was with Okular? And if possible, how? I haven't changed anything in the Kile settings when I made the Acrobat Reader the default viewer, just chnaged Okular to Acrobat Reader. Thanks a lot in advance.

---

### Post by ohzopants on 2009-07-24
That's actually a feature of Okular: it checks the file periodically to see if it has changed.  I don't think acroread has a similar feature.  The default gnome pdf viewer (I forget what it's called) does have this feature.

---

### Post by XCan on 2009-07-24
Evince is the default viewer in gnome. :) It works alright, but can make some stupid mistakes when printing by not distinguishing between colorboxes and colorboxes from bookmarks. :p

---

### Post by gemm on 2009-07-24
Thank you very much for the answers. I have switched back to Okular, however, now I cannot compile :(. When I press PDFLaTeX I do get

[PDFLaTeX] 0 errors, 3 warnings, 19 badboxes

on the Log and Messages window in Kile, which should show that the compilation process should be OK. However, when I press ViewPDF, I get the error message:

[ViewPDF] The file /home/Documents/ma_thesis/latex/MAThesis.pdf does not exist; did you compile the source file?

Yes, I did, but nothing seems to have happened.

I reinstalled Kile. The error is the same. Also, nothing of the other compilation tools works: when I try to compile to DVI, I get the following message:

[LaTeX] MAThesis.tex => MAThesis.dvi (latex)
[LaTeX] finished with exit status 1
MAThesis.tex:0: No hyphenation patterns were loaded for(babel) the language `German'(babel) I will use the patterns loaded for \language=0 instead.
MAThesis.tex:0: Label `table:nonlin' multiply defined.
MAThesis.tex:58:Cannot determine size of graphic in TreeBlue.jpg (no BoundingBox). \includegraphics[height=20mm]{TreeBlue.jpg}
MAThesis.tex:60:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:90:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:140:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:207:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:0:Underfull \vbox (badness 1701) has occurred while \output is active []
MAThesis.tex:212:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:215:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:218:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:221:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:224:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:238:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:0:Underfull \vbox (badness 1242) has occurred while \output is active []
MAThesis.tex:303:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:314:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:333:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:339:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:355:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:357:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:438:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:472:Underfull \hbox (badness 10000) in paragraph
MAThesis.tex:0: There were multiply-defined labels.
[LaTeX] 1 error, 3 warnings, 20 badboxes


What should I do to make things work again? In Settings --> Configure Kile ... --> Tools --> Build --> PDFLaTeX I have for Command: okular, and Options: -src -interaction=nonstopmode '%source'

What should I change? Or may be uninstall, and then reinstall Kile? However, as I said, I have just reistalled Kile though the Synaptic Package Manager. Thank you very much in advance.

---

### Post by XCan on 2009-07-24
Thas log file is kind of hard to define which the error is (I would guess it the .jpg). You should try and run pdflatex from terminal, it will be very clear then where it gets stuck.

---

### Post by gemm on 2009-07-25
> **XCan said:**
> Thas log file is kind of hard to define which the error is (I would guess it the .jpg). You should try and run pdflatex from terminal, it will be very clear then where it gets stuck.

Thank you for the suggestion. Everything seems to be Ok now. 

However, the Kile editor seems not to work as before any more - using Okular, the document is not automatically updated when I press PDFLaTeX (from Kile). It got updated with Okular automatically before, and I didn't need to close and open the document everytime I want to see my changes. Moreover, when I press PDFLatex, not everytime the changes are made. I don't know why. After I switched from Okular to Acrobat Reader, and then back to Okular, Kile is behaving very strangely:(. I don't know anymore what it does and when. I have tried to reinstall it, but it didn't help; then I removed the program, and installed it again, with the hope to obtain the very first default setting, which made Okular and Kile work as before. However, it is not working as before. Does Ubuntu remembers something about them? Do I have to delete some files somewhere? 

If somebody can help me with this, I will be very grateful. The previous working of Kile and Okular was very convenient. I do really prefer Acrobat Reader better than Okular, however, somebody has written above that Acrobat Reader does not have this function of automatic update of the PDF file as Okular does. Therefore I would prefer Okular with the automatic update before Acrobar Reader with not automatic update. But at the moment Okular has lost its function.

---

### Post by XCan on 2009-07-25
I only used Kile once and hated it, but anyway, have you tried to change Okular for Evince? I use Evince as viewer when I edit latex files in gedit + latexplugin.

---

### Post by Whiffle on 2009-07-25
> **gemm said:**
> Thank you for the suggestion. Everything seems to be Ok now. 

However, the Kile editor seems not to work as before any more - using Okular, the document is not automatically updated when I press PDFLaTeX (from Kile). It got updated with Okular automatically before, and I didn't need to close and open the document everytime I want to see my changes. Moreover, when I press PDFLatex, not everytime the changes are made. I don't know why. After I switched from Okular to Acrobat Reader, and then back to Okular, Kile is behaving very strangely:(. I don't know anymore what it does and when. I have tried to reinstall it, but it didn't help; then I removed the program, and installed it again, with the hope to obtain the very first default setting, which made Okular and Kile work as before. However, it is not working as before. Does Ubuntu remembers something about them? Do I have to delete some files somewhere? 

If somebody can help me with this, I will be very grateful. The previous working of Kile and Okular was very convenient. I do really prefer Acrobat Reader better than Okular, however, somebody has written above that Acrobat Reader does not have this function of automatic update of the PDF file as Okular does. Therefore I would prefer Okular with the automatic update before Acrobar Reader with not automatic update. But at the moment Okular has lost its function.

It stores its settings in your home directory, and by default the uninstaller doesn't remove those files when it runs.  

```

sudo apt-get purge kile

```
will remove the program AND the config settings, then you can reinstall it and it will be back to defaults.

---

### Post by gemm on 2009-07-25
> **XCan said:**
> I only used Kile once and hated it, but anyway, have you tried to change Okular for Evince? I use Evince as viewer when I edit latex files in gedit + latexplugin.

Hi,

I have just tried to change Okular to Evince in Kile :).

However, Kile continues to open the PDF document with Okular, and not with Evince. I have written about this in the Kile forum on the SourceForge.net, but I still don't have an answer from there. I am pasting below the message, which I have sent there, if you want to have a look. By the way, Evince looks really nice, I haven't used it before.


My message on SourceForge:

Hello, 
 
Is it possible to make Kile work with Evince on Ubuntu (Evince is the default viewer in gnome)? 
 
I have written in Settings --> Configure Kile ... --> Tools --> Build --> PDFLaTeX: 
 
Command: evince 
 
and I have left the options as they were: 
Options: -src -interaction=nonstopmode '%source' 
 
However, Kile continues to open the PDF document with Okular.  
 
(Moreover, when I press PDFLaTeX, and then ViewPDF, the old PDF file is opened - the new changes, which I have done in the tex file, are not present. This might be a problem of another issue, but I have it nevertheless, and therefore mention it here.)  
 
Thank you.

---

