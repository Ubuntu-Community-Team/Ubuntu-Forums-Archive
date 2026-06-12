---
title: "Open Office Spreadsheet link to files"
date: 2009-09-11
forum: General Help
---

### Post by andyklaj1985 on 2009-09-11
Hi Guys

I have a question that i hope you can answer

Problem:
I have a large collection of files that i have in oo's spreadsheet that i want to link to external files.

I know you can create a link manually, but because of the large number of files i just want a formula that i can drag down.

The closest thing to a solution that i have found is the HYPERLINK function, but i believe this will only link to URLs.

Does anyone have  a solution for me???

thanks in advance,

andy

---

### Post by andyklaj1985 on 2009-09-11
Figured it out - you need to use =hyperlink("file:........")

---

### Post by DaithiF on 2009-09-11
Hi,
you can use hyperlink to link to files too.
e.g.:
```
=hyperlink("file:///home/you/somedir/somefile.txt", "somefile.txt")
```
and if the filename is in a cell, say a1, then you could do:
```
=hyperlink("file:///home/you/somedir/" & A1, A1)

```

---

