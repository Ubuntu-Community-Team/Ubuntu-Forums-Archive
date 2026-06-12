---
title: "PDF reader choices"
date: 2010-08-06
forum: General Help
---

### Post by Kappity on 2010-08-06
Using Ubuntu 8.04.  Up until now, either Evince or Document viewer have been fine for my Linux PDF reader needs.  Just got a multi-section PDF document, a reference for one of my hobbies.  Besides the different documents with the actual information, there is a table of contents document that links to parts of the other PDF documents.  So if I want to look up something in the Ps, I don't have to go looking for the P section, I can just click on P in the table of contents, and it will link me to the correct part of the correct individual PDF file.

That's how it works using Preview on my Mac with Snow Leopard.  In Ubuntu, neither Evince nor Document Viewer will recognize the table of contents section as a valid PDF, even though it has a .pdf extension.  So I can't use the table of contents on my Ubuntu computer.

I've downloaded Adobe Acrobat, figuring it will work, but before I install it, have I got other PDF reader choices that might do the trick?

---

### Post by mali2297 on 2010-08-06
There are epdfview and okular, but they both use the same backend as evince: [poppler]("http://poppler.freedesktop.org/").

To investigate the problem, you can try running the following commands in the terminal:
```

file yourdocument.pdf
pdfinfo yourdocument.pdf

```
The first command tries to identify the file type based on its [magic number]("http://en.wikipedia.org/wiki/File_format#Magic_number"). The second command should show meta information such as author, title and PDF version.

---

### Post by mike555 on 2010-08-06
If those don't work for you , you might try "xournal".

---

### Post by Kappity on 2010-08-07
> **mali2297 said:**
> There are epdfview and okular, but they both use the same backend as evince: [poppler]("http://poppler.freedesktop.org/").

To investigate the problem, you can try running the following commands in the terminal:
```

file yourdocument.pdf
pdfinfo yourdocument.pdf

```
The first command tries to identify the file type based on its [magic number]("http://en.wikipedia.org/wiki/File_format#Magic_number"). The second command should show meta information such as author, title and PDF version.

Thanks.  The short version is that I have a work around.  The long version follows.

When I tried those commands, I got the message " ERROR: cannot open `WELCOME.pdf' (No such file or directory)".  I tried the same commands with the other pdf files in the same directory just to make sure I had the command right, and it worked for them.  The file WELCOME.pdf shows when I cd to the directory and type "ls", so something strange is going on.  Also, it shows in the GUI when I navigate to that directory, but the icon is different from the other pdfs in there.

It's really not vital, but I appreciate the advice.  I tried xournal, as suggested by mike555 below (should have said above), then caved in and installed Acrobat reader.  It wouldn't open the WELCOME.pdf either.  However, I discovered that there was another file named "TOC.pdf" which did work as a link to the other pdf files.  The instructions that came with this set of files said to use the WELCOME file to access the others, and that's what worked in Mac OSx.  Apparently when you open the file there it sends you to the TOC (table of contents) file but I guess in Linux something about it won't work, and you have to click on TOC directly.

Also, the links in the TOC document only seem to work in Adobe, not in evince or document viewer.

Anyway, now I can use the reference more or less the way it's supposed to be used, and if I want to understand any more, I'll just have to do some more reading.

---

