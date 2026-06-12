---
title: "Package that converts xls to csv or txt"
date: 2012-06-18
forum: General Help
---

### Post by cheerPuncH on 2012-06-18
Hi, 

I would like to know if anyone knows of a ubuntu 12.04 package that converts an xls file to something more manageable, like a csv or a txt file? This would prevent me from opening excel and doing the conversion to dramatically reduce run time. I know that catdoc use to be able to do a xls2cvs conversion, but I have Precise and after reading the man pages, it doesn't seem to hold that magical capability any more.

Thanks!

---

### Post by sudodus on 2012-06-18
You can use {Open Office / Libre Office} Calc in the same way as you would use Excel. (I just tested it with OO Calc in Ubuntu 10.04 LTS.)

*Edit:* Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

### Post by vasa1 on 2012-06-18
> **cheerPuncH said:**
> ...

Just use the thread tools near the top right of your post to mark the thread solved.

---

### Post by greenpeace on 2012-06-18
Check the package "Wordview" in the ubuntu software centre... from it's page:

"...Also provided is **xls2csv**, which extracts data from Excel spreadsheets and outputs it in comma-separated-value format..."

---

### Post by greenpeace on 2012-06-18
> **greenpeace said:**
> Check the package "Wordview" in the ubuntu software centre... from it's page:

sorry ... scratch that, I've just seen that the package name is "catdoc" as you put...

---

### Post by cheerPuncH on 2012-06-18
Hey! Thanks for the response. Catdoc dose have xls2cvs, but I don't know the correct way to enter it into the terminal. Sometimes it works with errors :/

Do you type
$catdoc xls2cvs file.xls temp.cvs?
When I do that I prints to STDOUT and states catdoc: No such file or directory.

If I do
$xls2cvs variants.xls table
I get the error
variants.xls is not OLE file or Error
table: No such file or directory

---

### Post by vasa1 on 2012-06-18
Could it be that you are trying to convert .xls files of varying complexity?

---

### Post by cheerPuncH on 2012-06-18
I'm not sure what you mean "varying complexity". The *.xls file isn't created by me. It's created by another software program as the output. I looked in the file. It's only 12 columns with about 120 rows. Do you know of another conversion package I could try?

---

### Post by sudodus on 2012-06-18
Did you try Libre Office Calc?

---

### Post by sudodus on 2012-06-18
> **cheerPuncH said:**
> Hey! Thanks for the response. Catdoc dose have xls2cvs, but I don't know the correct way to enter it into the terminal. Sometimes it works with errors :/

Do you type
$catdoc xls2c file.xls temp.cvs?
When I do that I prints to STDOUT and states catdoc: No such file or directory.

If I do
$xls2csv variants.xls table
I get the error
variants.xls is not OLE file or Error
table: No such file or directory
It writes to standard output, which you can redirect to temp.csv
```

catdoc file.xls > temp.csv
xls2csv file.xls > temp.csv

```

And as indicated by *vasa1*, variants.xls may be too complicated or simply damaged. It cannot be read by xls2csv.

*Edit:* I don't know if the two commands are different or simply aliases for the same program code, so try if one of them is better!

---

### Post by cheerPuncH on 2012-06-19
I would use Libre Calc, but I'm trying to pipeline data. It turns out there are two xls2csv with the same name [http://vinayhacks.blogspot.com/2010/04/converting-xls-to-csv-on-linux.html](http://vinayhacks.blogspot.com/2010/04/converting-xls-to-csv-on-linux.html). Since it wouldn't convert, I ended up chopping up another file format. I believe xls formats save more information about the data than just the data itself (like in xml), but I'm not too certain. Thank for all the help. I'm going to mark this solved.

---

### Post by sudodus on 2012-06-19
Yes, xls files also contain information about formatting (fonts and sizes, alignments etc), and probably can contain many other things for example macro code instructions.

It would be interesting and valuable for the Ubuntu Forum users to know how you solved your problem. What file format did you choose, and how did you convert to that format?

---

