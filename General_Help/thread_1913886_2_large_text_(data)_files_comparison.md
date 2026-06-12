---
title: "2 large text (data) files comparison"
date: 2012-01-23
forum: General Help
---

### Post by zeiz on 2012-01-23
I have large text file (10Mb) with about 77,000 of records.
Being opened in gedit it shows 4 columns with text and numbers in each.
It is not .csv or other delimited file but it can be opened in Calc as "fixed width columns" one.
Actually it's a product list and each record contains sku, part#, title and a string where quantity and prices are given. 

The content of the file changes daily and I must record the changes somehow. Online comparison is not an option.
I'd like to have a new file that would contain only those records which have been changed.

I tried **diff** in terminal but it outputs enormous amount of records that look identical: no changes could be noticed. 
Even more: the 4th column with most important data doesn't show at all.
Also with **diff** I couldn't find how to print the output to new file.

Is any other tool around here to compare 2 files and output to new file only those records which have been changed?

---

### Post by cortman on 2012-01-23
> **zeiz said:**
> I have large text file (10Mb) with about 77,000 of records.
Being opened in gedit it shows 4 columns with text and numbers in each.
It is not .csv or other delimited file but it can be opened in Calc as "fixed width columns" one.
Actually it's a product list and each record contains sku, part#, title and a string where quantity and prices are given. 

The content of the file changes daily and I must record the changes somehow. Online comparison is not an option.
I'd like to have a new file that would contain only those records which have been changed.

I tried **diff** in terminal but it outputs enormous amount of records that look identical: no changes could be noticed. 
Even more: the 4th column with most important data doesn't show at all.
Also with **diff** I couldn't find how to print the output to new file.

Is any other tool around here to compare 2 files and output to new file only those records which have been changed?

```
diff file1 file2 > results.txt
```

will save the output of the differences in a file called results.txt. Or if you want to view the differences in the terminal AND save them to file, use

```
diff file1 file2 | tee results.txt
```

---

### Post by pbrane on 2012-01-23
**meld** is a GUI diff program. It's in the repos.

---

### Post by Wayne_V on 2012-01-23
if you think there may be differences in white space or carriage control in the files you can play around with those options --- see 'man diff'

---

### Post by prshah on 2012-01-23
> **zeiz said:**
> 
I tried **diff** in terminal but it outputs enormous amount of records that look identical: no changes could be noticed. 

diff is your best bet. However, there are a number of options that you may require to get the output you want. For example, you may consider some of these options:

-i # ignore case

-E # ignore changes in tab expansion
-b # ignore changes in whitespaces between text
-w # totally ignore all whitespaces

--supress-common-lines 
--speed-large-files

You will have to play around with the options to see what suits you best, since it's hard to make a recommendation without seeing the data involved.

You have already seen how to redirect the output to file/file+screen.

Hope this helps

---

### Post by zeiz on 2012-01-23
Many thanks guys! It's really the best forum on WWW.
The data looks like this:
```
ab141001                   14-1001                    snowmobile chain case bearing & seal kit                      y0000249500001497kit
cc1066                     1066                       arctic cat custom cover                                       10000695000005213ea
107396                     31.3607                    prox camchain gsr600 '07-08 + gsx-r600 '01-09 + gsx-r750 '06  n0000769700005003ea
```
It's actually 4 columns with text (no headers). However the 3rd column (title) may look like a number of columns. The most important is the 4th column with strings where 1st char is a quantity in stock: Y means >9, a number - actual quantity and N-out of stock.
I tried **-y** switch to have "side-by-side" look that is just perfect for me. But it shows only 3 columns and even in 3rd column it shows only first word.
However I need all the columns side by side: I can then just open the diff file in Calc and I'm almost done!

---

### Post by Wayne_V on 2012-01-23
if you do a side-by-side the default page width is 130 so each file will be cut at 65 columns.  use "-W <num>" to increase that to fit both files.

---

### Post by zeiz on 2012-01-23
Thank you. I just tried **-yW 300** (200 wasn't enough) and I got all the columns! 
However new problem appeared: the output file cannot be opened in Calc correctly: some strings go to wrong sells.

In meantime I tried **meld**.
Result looks just great: 2 panes side by side, everything is in place, changes are highlighted, just copy the highlighted... no way to copy! 
Perhaps I'm missing something.:(

---

