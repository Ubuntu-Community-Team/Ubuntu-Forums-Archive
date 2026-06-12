---
title: "pdftotext - missing zeros"
date: 2009-12-15
forum: General Help
---

### Post by GOwin on 2009-12-15
I have several multi-page PDF files from which I need to extract columns of numbers from certain pages.

I used pdftotext to convert the page to plain text but dashes in the columns are not converted to zeros nor copied as dashes.

Attached is a sample portion of the data. When converted using pdftotext, I only get the following for the first column of numbers in the attached picture.

1,106 420 20,062 200 14 1 538 5 1 34 11 6 344 3 62 130 2 78 1 119

Instead, I expect dashes to be included

1,106 420 20,062 200 14 - - 1 538 5 1 - 34 11 6 344 3 62 130 - 2 - - - - - -78 1 119

or, at least zeroes

1,106 420 20,062 200 14 0 0 1 538 5 1 0 34 11 6 344 3 62 130 0 2 0 0 0 0 0 078 1 119

How do I get those dashes or zeroes in there?

---

### Post by junapp on 2009-12-15
great question.
I was going to suggest the -layout option but I think you'd end up with the same sort of problem just transposed (if pdftotext continues to remove the dashes).

---

### Post by kaibob on 2009-12-15
> **GOwin said:**
> I used pdftotext to convert the page to plain text but dashes in the columns are not converted to zeros nor copied as dashes.

Just a guess but perhaps it has something to do with the encoding used. Enter the following to view available encoding and test a few to see if they help.

```
pdftotext -listenc
```

---

### Post by GOwin on 2009-12-15
I tried the -layout option, it does get the dashes back but it also changes the layout of the numbers. I could probably work around with this option but I'd rather have the numbers as a single line. 

using -listenc option, I get the following:
UCS-2
ASCII7
Latin1
UTF-8
ZapfDingbats
Symbol

---

### Post by kaibob on 2009-12-15
I made a test pdf document with columns that contained both numbers and dashes and ran some tests. I encountered the same problem as you describe. Changing the encoding did not help. If you want all of the data in one very long line, you could use the -layout option and then pipe the output through the tr utility. The following worked for me but your document may be different. 
 
```
pdftotext -layout file.pdf - | tr '\n' ' ' | tr -s ' ' > file.txt
```

There should be an easier solution, but it escapes me. Perhaps another forum member will be able to help.

---

### Post by GOwin on 2009-12-16
Thanks. I took the -layout route and wrote a parsing script for data handling.

---

