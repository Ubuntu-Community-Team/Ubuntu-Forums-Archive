---
title: "multi-column PDF -&gt; single column"
date: 2010-04-01
forum: General Help
---

### Post by GNU Gnerd on 2010-04-01
Howdy folks,

As the title says, I'm looking for a good tool to take a multiple-column PDF and put the text all in one column.  Whether it ends up as a new PDF or a plain text file or whatever else doesn't matter, as long as it's in one column (though a command-line tool would be nice for automation).  

All of the methods I've seen and tried screw up somehow.  Copying and pasting the PDF's text into a text editor/OpenOffice copies the first line of the first column, then the first line of the next column, then the second line of the first column, and so on, like so:
```
AAAA   BBBB
AAAA   BBBB
AAAA   BBBB
```

becomes either this:

AAAABBBB
AAAABBBB
AAAABBBB

or this:
AAAA
BBBB
AAAA
BBBB
AAAA
BBBB

pdftotext interleaves the columns if there are multiple sections on one page, like so:

```

***AAAAA***	BBBBB	CCCCC
AAAAA	BBBBB	CCCCC
AAAAA		CCCCC
AAAAA	***CCCCC***	
AAAAA	CCCCC	***DDDDD***
	CCCCC	DDDDD
***BBBBB***	CCCCC	DDDDD
```

becomes

***AAAAA***
AAAAA
AAAAA
AAAAA
AAAAA
BBBBB
BBBBB
CCCCC
CCCCC
CCCCC
***CCCCC***
CCCCC
CCCCC
CCCCC
***DDDDD***
DDDDD
DDDDD
***BBBBB***

So does anyone know of a program that'll change it to a single column correctly?

---

