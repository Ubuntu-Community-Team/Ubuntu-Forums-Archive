---
title: "Searchable PDFs on Linux"
date: 2012-05-31
forum: General Help
---

### Post by chrislynch8 on 2012-05-31
Hi,

Does anyone know of a tool available on Linux (command line) that would be capable of converting a scanned PDF document into a searchable PDF document.

I don't need to convert them to editable documents, just the ability to search through them once scanned. Its a network scanner that will just dump scanned PDFs into a specific location on the the Ubuntu File Server.

Rgds
Chris

---

### Post by traditionalist on 2012-05-31
Recoll does this;

[http://www.lesbonscomptes.com/recoll/](http://www.lesbonscomptes.com/recoll/)

you can use it from the command line if you wish.

---

### Post by chrislynch8 on 2012-05-31
Hi, thanks for the link I will have a look at that.

So if I scan 100 documents as PDF to the server, this could be configured to make them all searchable by text contained inside the document, so if a user opens the file on there Windows PC there can in theory search for specific words, etc..

Rgds
Chris

---

### Post by traditionalist on 2012-05-31
> **chrislynch8 said:**
> Hi, thanks for the link I will have a look at that.

So if I scan 100 documents as PDF to the server, this could be configured to make them all searchable by text contained inside the document, so if a user opens the file on there Windows PC there can in theory search for specific words, etc..

Rgds
Chris

Yes.

[[IMG]http://img708.imageshack.us/img708/8287/recoll001.th.png[/IMG]]("http://img708.imageshack.us/i/recoll001.png/")


[[IMG]http://img812.imageshack.us/img812/6198/selection001p.th.png[/IMG]]("http://img812.imageshack.us/i/selection001p.png/")

[[IMG]http://img99.imageshack.us/img99/63/selection001f.th.png[/IMG]](http://img99.imageshack.us/i/selection001f.png/)

---

### Post by notbitmonk on 2012-05-31
I think that what you mean is a tool to perform optical character recognition on an image pdf. An image pdf is a pdf that has no text layer even if the scanned document was, for example, a letter. What I saw of recoll makes me think that the text layer has to exist. 
If what you mean is OCR, you can try gscan2pdf ([http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)). It is in the repositories. OCR is done by Tesseract ([http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/)). gscan2pdf get the scan from a regular scanner or you can import images like tif, png and even pdf's. Afterwards, you tell the software to perform OCR on the document. The text can be saved as a separate text file or inserted as a comment in a pdf. That last bit is the sad part. People will not be able to select text from the image which might be confusing to some. Tesseract also has several languages. If you are not doing OCR for English text, look for the appropriate language pack.

---

### Post by traditionalist on 2012-05-31
Recoll extracts the text from scanned PDF images. Although you could of course use gscan2pdf to begin with if you are scanning the stuff yourself.

---

### Post by medoc92 on 2012-05-31
> **traditionalist said:**
> Recoll extracts the text from scanned PDF images. Although you could of course use gscan2pdf to begin with if you are scanning the stuff yourself.

Hi, Recoll author here.

While I am very flattered by your trust in recoll :) , I don't want the original poster to be disappointed: no, recoll does not currently run OCR on image pdfs to extract text. 

I think that the suggestion above to run a  scan+OCR program is the right approach. 

Additionally, if the OCR'd text is stored by the suggested program in a PDF comment, I am not too sure that it would be indexed (maybe it would, I just don't know).  There could be a need to fix the pdf filter, but this would be quite easy as it is just a shell script which calls pdftotext (from poppler). I hope that a combination of pdftotext and pdfinfo should be able to extract whatever text exists inside a pdf.

Cheers,

jf

---

### Post by chrislynch8 on 2012-06-01
Hi All,

Thanks for the comments,

Looking at recoll as the author has suggested is not suitable. gscan2pdf seems to require a GUI to work, we use XP workstations connected to the Ubuntu File Server. I will play around with command line and see if it will be suitable.

So as to not confuse things this is the goal.

1: The User loads all paper on the scanner and enters their keycode. All pages are scanned as pdf files to a specific location on the File Server

2: Some application is monitoring this folder run OCR on all files and converts them to searchable pdf files.

3: The User then accesses the shared folder and moves all the converted files into the relevant locations and accesses them as and when needed with some PDF reader.


If this automatic approach is not possible, it will be a case of finding the best windows based software to achieve this, already have tested paperport+omnipage which works perfect but this is expensive.

Thanks again for the replies and I will post back if gscan2pdf achieves what I'm looking for.

Rgds
Chris

Quickly looking at gscan2pdf looks like a GUI interface is required. I've just Ubuntu Server cli only...

---

