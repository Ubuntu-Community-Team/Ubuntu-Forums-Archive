---
title: "pdftotext column order"
date: 2009-12-19
forum: General Help
---

### Post by GNU Gnerd on 2009-12-19
Howdy all.

I need to convert a bunch of PDFs to text files so I can more easily manipulate them, and I've found that pdftotext handles files just fine if they have a single column of text.  However, some of my files have two or three columns, and those files aren't converted as I'd like.  Running pdftotext on a two-column pdf can get the column order wrong if the headers are at different height; for instance, in the following:

```
		***2222222222***
***1111111111***	2222222222
1111111111	2222222222
1111111111	2222222222
1111111111	2222222222
```

instead of putting the second column after the first, it puts the second column first:

```
***2222222222***
2222222222
2222222222
2222222222
2222222222

***1111111111***
1111111111
1111111111
1111111111
```

And with the three-column PDF, it interleaves the columns and sometimes separates the sections based on which section headers come first vertically, turning this:

```

***AAAAA***	BBBBB	CCCCC
AAAAA	BBBBB	CCCCC
AAAAA		CCCCC
AAAAA	***CCCCC***	
AAAAA	CCCCC	***DDDDD***
	CCCCC	DDDDD
***BBBBB***	CCCCC	DDDDD
```

into this:

```
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
```

I've tried using the -layout flag, but that just leaves the columns as they are with a bunch of extraneous whitespace, which would make things hard to work with anyway.

Any ideas on how to force it to put the columns in the order they're supposed to have, or any other PDF-to-text utilities that'll do that easily?

---

### Post by GNU Gnerd on 2009-12-28
No one has any ideas?

---

