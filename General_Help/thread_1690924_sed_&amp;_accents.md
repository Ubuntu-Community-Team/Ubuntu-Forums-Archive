---
title: "sed &amp; accents"
date: 2011-02-19
forum: General Help
---

### Post by jmvidalvia on 2011-02-19
Hi, 
I need to import a file into a mysql database. As the fields are "single space separated" I am adding a tab to allow the mysql import function "load data infile" work.
But, when executing the following code...
```
sed 's/./\t/'${num} $FILEin > $FILEout
```
...everytime sed finds an accent counts the letter as two, so tabs are wrongly inserted.
¿is there any way sed can understand that special characters are just one letter?
Thanks a lot!

NOTE: I tried to use iconv to convert the file to a different codification, but letters with accents are simply removed, so I have the same problem.

SOLVED: I checked the input file encoding with $file before runnign iconv, and now all is ok.

---

