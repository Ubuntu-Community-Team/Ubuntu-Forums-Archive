---
title: "How to scan large amounts of paper efficient?? scan, review, ocr settings???"
date: 2011-01-16
forum: General Help
---

### Post by kaktux on 2011-01-16
I just finished my master and now got some time. 
I won´t need most of my scripts and notes much often anymore - but don´t want to jsut throw them away.  

Thats why i plan to scan all of them. 
Should be a few thousand pages. I just bought me a HP Scanjet 5590 which has a document feeder and can also handle duplex scans if wanted.  

So now my question is: 
Which programms (i am using Kubuntu 10.10) do you recommand - and which settings (like solution - mostly i read that 300dpi is enough) should be the best for doing so?? 
Also after scanning i want to review the scan - and if needed alter it (as if i would correct it with gimp). 
Later on OCR would be nice - so you can search the documents.  

So far i tried out gscan2pdf - but didn´t find good unpaper options yet - and also not so good results with ocr (tried cuniform - but read that ocropus is the best today). 
But i read that xsane my give better results. or maybe there´s an even better solution.  

Another issue is the saving format. pdf, djvu or simply pack images (in this case again - best format??) to a container (like cbr).  

Do you have any experience in scanning bigger amounts of paper?? What programms/ what settings would you recommand??  

I´m thankful for any hint!!

---

### Post by astrobob.tk on 2011-05-05
> **kaktux said:**
> 
So now my question is: 
Which programms (i am using Kubuntu 10.10) do you recommand - and which settings (like solution - mostly i read that 300dpi is enough) should be the best for doing so?? 
Also after scanning i want to review the scan - and if needed alter it (as if i would correct it with gimp). 
Later on OCR would be nice - so you can search the documents.  

So far i tried out gscan2pdf - but didn´t find good unpaper options yet - and also not so good results with ocr (tried cuniform - but read that ocropus is the best today). 
But i read that xsane my give better results. or maybe there´s an even better solution.  


I also did not like gscan2pdf at first, but now am using it again; now having a problem with opening a previously scanned & saved Tiff file of 47 pages but I think I will find a solution online for that later on.

My advice is give it a try. The nice thing is that you can edit (i mostly use crop) after scanning a page; furthermore under "Tools" there are some more options besides crop & that includes Gimp, which seems to be of ur interest.

Resolution: I mostly use 600 dpi as my default but 300dpi for regular text free of color &/or complicated figures is great.

OCR: though Tesseract has a good reputation out there but my first impression was not that good. Alternatively you can use [http://any2djvu.djvuzone.org/](http://any2djvu.djvuzone.org/) to ocr your document (note that the document will be converted to a djvu file but you can then use a software like djvusmooth to convert it to pdf).

Other softwares I know about: Simple Scan (default in Ubuntu i guess)

I also recommend you install & try "Scan Tailor" in case you wish to clean & post-process your scans. Give it a try. Its really great. The only backdraw of it is that it imports .tiff only (which btw can be saved in gscan2pdf as 1 file containing several pages).

> **kaktux said:**
> 
Another issue is the saving format. pdf, djvu or simply pack images (in this case again - best format??) to a container (like cbr).  

Do you have any experience in scanning bigger amounts of paper?? What programms/ what settings would you recommand??  

I´m thankful for any hint!!

What I do: I usually scan with gscan2pdf (cropping the pages as I go to   get rid of any black parts due to the pages being smaller than the   scanner surface, particularly the top & bottom ones). I then save   the scanned pages in a .Tiff document which I import (New project) to   scan tailor & do the post processing then output the result (will be   individual .tiff files). Then I re-import those files to gscan2pdf    save them in djvu (very good to saving space & preserving quality)   or pdf.

---

