---
title: "Signing a PDF"
date: 2012-03-13
forum: General Help
---

### Post by Jeroen De Dauw on 2012-03-13
I need to sign (written signature, not a digital one) a bunch of PDFs.  Is there a tool for Ubuntu that allows doing this? Preferably by  letting my draw my signature using the cursor, or alternatively simply  by inserting an image. And it ought to be able to insert text (typed, not written) as well so I can put a date on it.

Googled for this and tried some stuff, but nothing worked properly. I'm thinking it can't be that hard to do this... So who can point me to some decent app? :)

---

### Post by 3Miro on 2012-03-13
This should install and run under wine:
[http://pdfedit.cz/en/index.html](http://pdfedit.cz/en/index.html)

Otherwise, you can try to convert the pdf to just an image, edit it with Gimp and convert back to a pdf. However, this will be a pdf image and not a pdf document, I don't know if it matters. Some things like fonts will no longer scale.

I don't know of any other ways.

---

### Post by Helen McCall on 2012-03-18
A ackage which will let you write freehand on pdf files is xournal.

I've tried it myself and find it works very well if you can write clearly using a mouse. A little practice might be needed to get your signature looking natural.

It also allows you to type text into the pdfs if you need to fill in forms.

---

### Post by nickrout on 2012-03-18
> **3Miro said:**
> This should install and run under wine:
[http://pdfedit.cz/en/index.html](http://pdfedit.cz/en/index.html)

Otherwise, you can try to convert the pdf to just an image, edit it with Gimp and convert back to a pdf. However, this will be a pdf image and not a pdf document, I don't know if it matters. Some things like fonts will no longer scale.

I don't know of any other ways.

There is a longer description here:

[http://zyliu2005.blogspot.co.nz/2009/08/linux-how-to-insert-img-to-pdf-files.html](http://zyliu2005.blogspot.co.nz/2009/08/linux-how-to-insert-img-to-pdf-files.html)

---

### Post by HermanAB on 2012-03-18
Use Gimp to add the signature to a page, then use PDFShuffler to stick the page back into the right spot in the PDF file.

---

### Post by nickrout on 2012-03-18
> **3Miro said:**
> This should install and run under wine:
[http://pdfedit.cz/en/index.html](http://pdfedit.cz/en/index.html)

Otherwise, you can try to convert the pdf to just an image, edit it with Gimp and convert back to a pdf. However, this will be a pdf image and not a pdf document, I don't know if it matters. Some things like fonts will no longer scale.

I don't know of any other ways.

Why install under wine? It is a unix programme and available in ubuntu.

---

### Post by 3Miro on 2012-03-18
> **nickrout said:**
> Why install under wine? It is a unix programme and available in ubuntu.

Wow, it is indeed. I didn't know that. I found this program some time ago and there were many links explaining how to install it under wine. I never actually used it at the time, but why would all those people have those links if there is a native version. Could it be that the Windows version comes with more "features"?

Looking at pdfedit at the repos should be the first step then.

---

