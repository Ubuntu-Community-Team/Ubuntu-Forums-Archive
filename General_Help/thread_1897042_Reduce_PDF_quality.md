---
title: "Reduce PDF quality?"
date: 2011-12-18
forum: General Help
---

### Post by jwbrooks0 on 2011-12-18
I'm using my netbook to view a fairly large and high quality pdf, but the load time for each page is annoying.  Is there a way for me to reduce the quality, convert to grayscale, etc so that the pages will load quicker?  And if so, how would I go about doing this?  

Thanks!

I'm fairly new to Ubuntu and overall inexperienced with Linux.

---

### Post by polki@mac.com on 2011-12-19
You could try xpdf. It's in the repo and is very fast. Not the best looking program, but it gets the job done!

---

### Post by sudodus on 2011-12-19
The instructions of this link work for me
[COLOR=RoyalBlue]_[http://www.ehow.com/how_6823473_reduce-pdf-file-size-linux.html](http://www.ehow.com/how_6823473_reduce-pdf-file-size-linux.html)_[/COLOR]
Use /screen for setting for smallest size but good enough for your screen

```
gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -sOutputFile=output.pdf input.pdf
```

---

### Post by mcduck on 2011-12-19
Imagemagick should do the trick as well. You could easily both convert to grayscale and drop the DPI to something more suitable for display use.

---

