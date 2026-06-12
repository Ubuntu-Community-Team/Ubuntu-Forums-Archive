---
title: "problem combining .pdfs"
date: 2011-03-05
forum: General Help
---

### Post by kooley on 2011-03-05
hello, im trying to combine some .pdf files and am having some issues. when i looked up how to combine them i found many things saying to use "ghostscript" so i decided to try it. when i put this command into my shell


"gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=AvengedSevenfold-BatCountry.pdf -dBATCH Avenged Sevenfold - Bat Country 1.pdf Avenged Sevenfold - Bat Country 2.pdf Avenged Sevenfold - Bat Country 3.pdf Avenged Sevenfold - Bat Country 4.pdf Avenged Sevenfold - Bat Country 5.pdf" 


i got this output and a blank pdf file


"Error: /undefinedfilename in (Avenged)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1150/1684(ro)(G)--   --dict:0/20(G)--   --dict:92/200(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript 8.61: Unrecoverable error, exit code 1"


can somebody help me, let me know what i can do?


thank you

---

### Post by TeoBigusGeekus on 2011-03-05
1)Install imagemagick
2)Open terminal and give
```
convert nameoffirstpdf.pdf nameofsecondpdf.pdf ..... nameoflastpdf.pdf nameoffinalcombinedpdf.pdf
```

---

### Post by kooley on 2011-03-05
thank you i will defiantly give that a shot :)

---

### Post by beew on 2011-03-05
The easiest way is to use pdfchain. Install it from the repo.

It is a GUI frontend for the pdftk. You add all the files you want to merge, make sure that they are in the correct order (if not just move them up or down using the button) and then press "merge' and that's it. The only limitation is that it can merge only upto 26 files so if you have more you would have to do it several times.

EDITED: It should have been press "save" in  the last step.

---

### Post by kooley on 2011-03-05
thank you for the suggestions :)

---

### Post by kooley on 2011-03-05
i tried to install pdfchain but it cant be found, i tried to install with the shell and with synaptic and cant find the package

---

### Post by beew on 2011-03-05
Just replied to your pm

EDITED: Just notice you are using kubuntu, maybe that's why you can't find it? I do think it has access to the same repositories though. Probably you have a pre Lucid release of Ubuntu,  in that case add the PPA I linked in my message.

Ok, I should post it here in case anyone else need it.
[URL="https://launchpad.net/%7Epdfchain-team/+archive/ppa"]
https://launchpad.net/~pdfchain-team/+archive/ppa[/URL]

---

### Post by rosencrantz on 2011-03-05
In this case, Imagemagick is just a frontend for gs, so that might not do the trick. I'd be suspicious about spaces in filenames - did you try enclosing the single filenames in quotes or renaming?

Cheers,
rosencrantz

---

### Post by kooley on 2011-03-05
i have solved the problem :) 

what i did was i renamed all 5 of the pdfs so that they had no spaces or dashes and it worked perfectly :) 
this was the finished code that finaly worked


"gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=AvengedSevenfold-BatCountry.pdf -dBATCH BatCountry1.pdf BatCountry2.pdf BatCountry3.pdf BatCountry4.pdf BatCountry5.pdf"

thank you all for your suggestions and help it is much appreciated

---

### Post by beew on 2011-03-05
I would still prefer pdfchain, I use it to merge ebooks that come with hundreds of loose pages. :) but glad that it works out for you.

---

