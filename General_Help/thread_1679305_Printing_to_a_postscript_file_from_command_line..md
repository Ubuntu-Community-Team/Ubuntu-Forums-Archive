---
title: "Printing to a postscript file from command line."
date: 2011-01-31
forum: General Help
---

### Post by Aikifuku on 2011-01-31
I just upgraded to 10.10 and am having trouble getting lpr to output a postscript file by default. I installed cups-pdf and that let me print to pdf by default using lpr. Is there a way to set up a printer using system -> administration -> printing that will print to a .ps file? The ghostscript packages are installed.

Thanks for any input on this.

---

### Post by anglican on 2011-02-01
> **Aikifuku said:**
> I just upgraded to 10.10 and am having trouble getting lpr to output a postscript file by default. I installed cups-pdf and that let me print to pdf by default using lpr. Is there a way to set up a printer using system -> administration -> printing that will print to a .ps file? The ghostscript packages are installed.

Thanks for any input on this.Not really an answer, but if I needed a postscript file I'd print to pdf then run pdf2ps on the output. How often do you need to do this?

H

---

### Post by Aikifuku on 2011-02-01
I may need to do this a bit. I have installed a Seismic processing system whose functions are supposed to output postscript files. When I pipe these commands to lpr a pdf is printed just fine. I think this is because lpr knows how to do the conversion from a .ps to a .pdf. However, if I pipe directly to evince or another postscript viewer I just get a blank window. I believe this is because I can not automatically print to a postscript file.

Thanks a lot for the response.

---

