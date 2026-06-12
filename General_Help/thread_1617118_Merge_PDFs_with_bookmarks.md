---
title: "Merge PDFs with bookmarks?"
date: 2010-11-09
forum: General Help
---

### Post by fhsm on 2010-11-09
I've got a collection of PDFs each of which has bookmarks in it (the things that populate the side panel of a PDF viewer). I'm trying to find a way on Ubuntu to concatenate these files into a single PDF that maintains working bookmarks. 

I've found solutions that remove the bookmarks all together and this command:
```

gs -q -sPAPERSIZE=letter -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile='Book_Title.pdf' chapters/*.pdf

```

which preserves the bookmarks but leaves them pointing to the wrong page. So for example a bookmark in chapter 2 that pointed to page 5 of the chapter 2 pdf when it was generated points to page five of the combined book pdf (which is in the introduction not chapter two...).

This isn't a question about getting the printed page numbers to work out. It's just about making the bookmarks link to the intended content.

Can anyone suggest a program or command to do this sort of combination?

Thanks!

---

### Post by zealibib slaughter on 2010-11-09
I don't know if it will do what you want or not but you may want to try PDF editor.  You can get it from synaptic.

---

### Post by fhsm on 2010-11-09
Thanks for the suggestion but I'm really looking for something I can run from the command line.

---

### Post by fhsm on 2010-11-09
*pdfsam* can merge a PDF and get the bookmarks correct! 

It has a command line interface as well *pdfsam-console* but it's a bit finicky about arguments.

I've found that: ```
pdfsam-console -f /full/path/to/chapt.pdf -f /full/path/to/anotherchapt.pdf -o /full/path/to/outputfile.pdf concat
``` works (this is not what the interactive help shows but whatever). 

The problem with this is that I want to be able to point it at a directory and have it merge everything in that dir into a PDF. Unlike *gs* in my OP it can't expand the *. 

Could someone suggest a command to generate the correctly formatted argument list or other way to accomplish this? Some sort of `` magic perhaps?

---

