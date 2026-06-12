---
title: "Cups-pdf"
date: 2010-12-31
forum: General Help
---

### Post by spmmoi on 2010-12-31
I need help with web-page  pdf printing from FireFox. I want to be able  to select portions of  text on the document to print as pdf for later  viewing on my machine. I  have the CUPS-PDF thing setup, however the  output file size is usually  larger. I wish to be able to reduce the  output file size.

When I used NitroPDF freeware on Windows, text from the web site is   usually under 1MB, but now, same materials would come out in 2MB or   more. 

I stumbled upon this [http://milan.kupcevic.net/ghostscript-ps-pdf/](http://milan.kupcevic.net/ghostscript-ps-pdf/)   While I think it may help, I do not know how to incorporate this into   my "cupsd.conf" file or to overwrite my existing print config and not screw   things over.

 Any ideas?

---

### Post by TeoBigusGeekus on 2010-12-31
Open your browser of choice and go to 
```
http://localhost:631/
```
Select printers, virtual_pdf_printer and fiddle with its settings, ie. reduce the quality of the output pdf.

---

### Post by spmmoi on 2010-12-31
Thanks for your reply. I opened that URL. Find attached what I see. Where do I find the Virtual PDF setting?

---

### Post by TeoBigusGeekus on 2010-12-31
There should be a printers button on the top of the page.
EDIT: Tiny detail - I'm on Arch.

---

### Post by spmmoi on 2010-12-31
> **TeoBigusGeekus said:**
> There should be a printers button on the top of the page.
EDIT: Tiny detail - I'm on Arch.


Thank you, I see it now. Its default is set to 150dpi. Does this explain why I have larger pdf file outputs? Do you know if I can add an extra option lower than 150dpi to the options list, say, 100dpi or lower still? This will help me a great deal. 

When I try to save the same web page on a Windows laptop using NitroPDF, I get a maximum of 700KB in output, and that's two pages. But with the cups-pdf option, just one page gives me some 1MB...

---

