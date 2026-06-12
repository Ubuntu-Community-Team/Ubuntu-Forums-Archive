---
title: "Evince+Code128 Font from internetzollanmeldung.de"
date: 2012-08-20
forum: General Help
---

### Post by hagos on 2012-08-20
Hi,

I am using Ubuntu 12.04.1 LTS with evince 3.4.0. I tried shipping abroad, with 

[https://www.ausfuhrplus.internetzollanmeldung.de/iaap/](https://www.ausfuhrplus.internetzollanmeldung.de/iaap/)

at the end of the process you get a pdf.
This pdf needs a Type1-font called "Code-128" which you can download from the website.
But the downloaded file contains a TrueType-font (code_128.ttf). So i copied it to 

```

/usr/local/share/fonts/truetype

```and ran

```

fc-cache -vf
dpkg-reconfigure fontconfig

```It worked fine for LibreOffice but viewing the pdf with evince still didn't show any barcode. So I tried to convert it using

```

ttf2ufm code_128.ttf

```and copied the resulting files to

```

/usr/share/fonts/type1/Code-128

```and ran the shell-commands again. Still evince didn't recognize the fonts.
When I run
```

fc-cache -vf

```I get
```

...
/usr/share/fonts/type1/Code-128: caching, new cache contents: 1 fonts, 0 dirs
...

```Other pdf-viewer like epdfview, okular, xpdf, ... also don't recognize the font.

What am I missing?

How can I use that font?

---

### Post by stef222 on 2012-11-02
For me only acroread works with this code128 font.
But this was the same situation with opensuse installations...
Steff

---

### Post by grahammechanical on 2012-11-02
What are you missing? You ask. Did you install this font on to the machine before or after you created this PDF document?

If you are creating this document in LibreOffice and then exporting it to PDF, you need to use that special font in the document before you export. 

Then when you export to PDF the special font will be embedded into the PDF document so that the font is rendered by the PDF reader application.

Regards.

---

