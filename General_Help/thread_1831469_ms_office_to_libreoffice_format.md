---
title: "ms office to libreoffice format"
date: 2011-08-23
forum: General Help
---

### Post by diospada11 on 2011-08-23
SOLVED. hi. i have a very brief question, why is it that my original ms office documents appear differently in libreoffice? i tried saving it as .docx, .doc, and .odt. they appear differently and they still don't show the PROPER formatting of my document. please help. :|


BR

SOLVED.


EDIT: how can i batch convert .docx files to .odt? i have tried downloading odfconverter but i receive error thus not being able to install it. please help me..

---

### Post by sanderd17 on 2011-08-23
Because:

[LIST=1]
[*]MS doesn't like ODT
[*]DOC and DOCX file types are very difficult to implement. Even MS makes serveral mistakes with the implementation of their own format.
[/LIST]

How can you solve it? Use a simple export format as PDF, but the disadvantage is that you can't edit PDFs that easy.

---

### Post by raja.genupula on 2011-08-23
Hi,
     i am still facing the format problems . thats  why i am using hotmail's online office for my doc applications .


PDF editor 

[http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html)

---

### Post by The Cog on 2011-08-23
You could simply be missing the required fonts. Make sure you have package **ttf-mscorefonts-installer** installed.

---

### Post by diospada11 on 2011-08-24
> **sanderd17 said:**
> Because:

[LIST=1]
[*]MS doesn't like ODT
[*]DOC and DOCX file types are very difficult to implement. Even MS makes serveral mistakes with the implementation of their own format.
[/LIST]

How can you solve it? Use a simple export format as PDF, but the disadvantage is that you can't edit PDFs that easy.

hmm.. in my scenario, i saved a .docx to a .odt using MS Office 2010. i tried opening it with MS office 2010, and it displayed correctly. but when i opened that .odt file using libreoffice, it still doesn't display correctly. :|

> **raja.genupula said:**
> Hi,
     i am still facing the format problems . thats  why i am using hotmail's online office for my doc applications .


PDF editor 

[http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html)

oh thanks for the link. i would try it a bit later.

> **The Cog said:**
> You could simply be missing the required fonts. Make sure you have package **ttf-mscorefonts-installer** installed.

i think i have already installed the latest.

"Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

i even copied my MS fonts from my windows desktop over to my ubuntu laptop. i believe it's working since i can use those fonts properly in libreoffice and other linux apps.

---

### Post by Mark Phelps on 2011-08-24
Sorry, but ".docx" files don't render well in anything except MS Office, version 2007 or later.  MS, like always, is not very forthcoming in what it does internally in its formats, and when the open-source community has to guess (in order to use MS formats), they don't always guess correctly.

If you're going to use ".docx" files a lot, you're going to be stuck using MS Office.  And, before you ask, MS Office 2007 DOES work with Wine, MS Office 2010 does not.

---

### Post by sanderd17 on 2011-08-24
MS did standardise docx, it's called the Office Open XML standard ([http://en.wikipedia.org/wiki/Office_Open_XML](http://en.wikipedia.org/wiki/Office_Open_XML)), not to be confused with the OpenDocument standard ([http://en.wikipedia.org/wiki/OpenDocument](http://en.wikipedia.org/wiki/OpenDocument)), used by OpenOffice.org and LibreOffice. 

But the problem is that the OOXML standard is very difficult. The specification isver 6546 pages, while the OpenDocument specification is only 867 pages. So MS could easely implement the correct OpenDocument format, but it is very difficult to correctly implement the OOXML format.

MS doesn't even implement the whole specification, only a subset of it. And the open source community has to guess what subset they have implemented to be compatible.

[http://en.wikipedia.org/wiki/Standardization_of_Office_Open_XML#Criticism](http://en.wikipedia.org/wiki/Standardization_of_Office_Open_XML#Criticism)

---

### Post by diospada11 on 2011-08-24
oh. i see. anyways, i found a solution by opening it with google docs. apparently, it shows the proper formatting of my document. anyways, i think i can recreate the current format in native libreoffice .odt so that i won't have any problems in the future since i made a complete move to ubuntu. (my windows 7 won't bootup. i don't know why :( )

THANKS FOR THE REPLY GUYS!



EDIT: i need more help please. how can i batch convert .docx files to .odt?

---

### Post by sanderd17 on 2011-08-24
If you say google docs can convert it properly, than you can use googlecl to convert them. 

It's a while ago since I last worked with googlecl, but it's pretty intuitive.

[http://code.google.com/p/googlecl/](http://code.google.com/p/googlecl/)

I believe 

```

google docs upload ~/to_be_converted/* --folder "bash_uploads" 

```

will do upload the docs in the "to_be_converted" directory to a folder called "bash_uploads". And

```

google docs get --folder "bash_uploads" --format odt ~/is_converted/

```

will download the converted docs back as .odt. Hopefully this will work as you wanted.

---

### Post by diospada11 on 2011-08-24
> **sanderd17 said:**
> If you say google docs can convert it properly, than you can use googlecl to convert them. 

It's a while ago since I last worked with googlecl, but it's pretty intuitive.

[http://code.google.com/p/googlecl/](http://code.google.com/p/googlecl/)

I believe 

```

google docs upload ~/to_be_converted/* --folder "bash_uploads" 

```

will do upload the docs in the "to_be_converted" directory to a folder called "bash_uploads". And

```

google docs get --folder "bash_uploads" --format odt ~/is_converted/

```

will download the converted docs back as .odt. Hopefully this will work as you wanted.

thanks for this. but somehow, google docs doesn't have some of the fonts used in some of my documents. aren't there some other alternatives? i have access to a windows 7 with microsoft office 2007 in my desktop.

---

### Post by sanderd17 on 2011-08-25
> **diospada11 said:**
> thanks for this. but somehow, google docs doesn't have some of the fonts used in some of my documents. aren't there some other alternatives? i have access to a windows 7 with microsoft office 2007 in my desktop.

I don't know any alternatives by heart, but I googled and found this: [http://www.oooninja.com/2008/01/convert-openxml-docx-etc-in-linux-using.html](http://www.oooninja.com/2008/01/convert-openxml-docx-etc-in-linux-using.html)

Does it help?

---

### Post by diospada11 on 2011-08-25
hi. i used odf-converter-integrator-strawberry. then i ran it using terminal. and it worked great! thanks guys!

---

