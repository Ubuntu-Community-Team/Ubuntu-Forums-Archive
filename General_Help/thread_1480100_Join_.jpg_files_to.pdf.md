---
title: "Join .jpg files to.pdf"
date: 2010-05-11
forum: General Help
---

### Post by JugglinPhil on 2010-05-11
I've got a collection of comics on my computer which consist of single images in .jpg. I am trying to join them all to a big .pdf, so that I end up with one e-book per comic instead of a bunch of single images.
Is there any program that can help me with that.
I already tried importing it to Open Office, but that way I will have to rescale every single image to fit a page, which would take ages.
Thanks.

---

### Post by kaibob on 2010-05-11
If a command-line solution is OK, you can use the convert utility from the imagemagick package. The command is: 

```
convert *.jpg output.pdf
```

Depending on the version of imagemagick used, you may have to specify the compression used to achieve reasonably-sized PDF files:

```
convert -compress Zip *.jpg output.pdf
```

The version of imagemagick installed prior to lucid had a bug that would cause the above command to fail. If that's the case, use graphicsmagick with the following command:

```
gm convert *.jpg output.pdf
```

---

### Post by Bonster on 2010-05-11
For comicbook you might want to compress it to CBR (WINRAR files) and install 'Comix' app to read. Don't use PDF

---

### Post by JugglinPhil on 2010-05-12
Nice, thank you.

---

