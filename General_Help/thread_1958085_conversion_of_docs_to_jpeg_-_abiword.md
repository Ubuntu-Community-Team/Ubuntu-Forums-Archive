---
title: "conversion of docs to jpeg - abiword?"
date: 2012-04-13
forum: General Help
---

### Post by mchahn on 2012-04-13
I need to convert arbitrary documents to jpeg.  Docs like msword and pdf.  I need to do this from the command line on my web server.

I've found abiword and it looks like a good fit for msword docs.  I see there is a plugin abiCommand that lets me batch run it from the command-line.

I've also found the "abi convert all to jpeg pro" which looks even better.  I can't find the equivalent to abicommand for that.

Anyone have any experience using abi products from the command line?  Does anyone know a better forum for this topic?

---

### Post by sudodus on 2012-04-13
If you want to do batch conversion, this is a way:

First make pdf files from documents
[[COLOR="Red"]_http://superuser.com/questions/156189/how-to-convert-word-doc-to-pdf-in-linux_[/COLOR]]("http://superuser.com/questions/156189/how-to-convert-word-doc-to-pdf-in-linux")

The you can use convert from ImageMagick to convert pdf files.
```
convert file.pdf file.jpg
```
And you can add options if you like.

I have not tried via Abiword, it might work well. Just try and find what is best for you :-)

---

### Post by mchahn on 2012-04-13
Thanks, that link gives a lot of options to try.  Also, I think some of those, like abi, can go straight to jpeg.

---

