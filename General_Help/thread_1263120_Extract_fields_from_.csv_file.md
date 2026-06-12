---
title: "Extract fields from .csv file"
date: 2009-09-10
forum: General Help
---

### Post by stallvalds on 2009-09-10
Hello everybody,
I'm trying to extract specific fields from a .csv file(last name and phone number). I can do it no problem in a normal text file, but cannot figure out how to do it in a csv file. I have to do this using only, paste, cut, sort or join commands through the terminal only. I'm using 9.04 Jaunty Jackelope. Any ideas?

---

### Post by fragos on 2009-09-10
The simplest way is to open the csv in openoffice spreadsheet, delete the columns you don't need and save as a csv under a new file name.

---

### Post by stallvalds on 2009-09-10
Yah I know, but I need to do it all through CLI. No GUI.

---

### Post by StuartN on 2009-09-10
Csvtool is a command line package with commands to extract, join and output. It should do everything you need. Install and then "csvtool --help"

---

### Post by stallvalds on 2009-09-10
Thanks!!

---

### Post by StuartN on 2009-09-10
Just in case it helps, the cut command might do what you want. For instance "cut -d, -f1,3 myfile.csv" would look for fields delimited by a comma and output the fields 1 and 3. It is on any Linux system, but doesn't select rows or join files.

---

### Post by stallvalds on 2009-09-10
Yes, but what exactly is the delimiter for a csv file?They're just columns.

---

### Post by stallvalds on 2009-09-10
perhaps I could do this with awk?

---

### Post by lisati on 2009-09-10
> **stallvalds said:**
> Yes, but what exactly is the delimiter for a csv file?They're just columns.

Hint: "CSV" stands for "comma separated variables" or "comma separated values"

In other words, if you think of a CSV as a simple text file, the different items on each line are separated ("delimited") by commas.

Have a look here: [http://en.wikipedia.org/wiki/Comma-separated_values](http://en.wikipedia.org/wiki/Comma-separated_values)

---

### Post by StuartN on 2009-09-10
> **stallvalds said:**
> Yes, but what exactly is the delimiter for a csv file?They're just columns.

The delimiter can be a comma (as in Comma Separated Value) but is very often a tab. The cut command uses tab as a default, so "cut -f1,3 myfile.csv" would give fields 1 and 3 if the file contains tabs and "cut -d, -f1,3 myfile.csv" would work with commas.

You could do the exact same in awk with:

```
awk -F "\"*,\"*" '{print $3}' file.csv
```

---

### Post by stallvalds on 2009-09-10
Thanks to stuart and lisati. That was exactly what I was looking for. what delimiter to specify was my main problem.

---

### Post by lisati on 2009-09-10
Glad to be of some help.

<aside>
One of my banks gives me a choice of downloading, amongst other options, transactions in both comma-separated and tab-separated formats. For the tab-separated version, it uses the ".tsv" extension for the file. I don't recall having seen the "tsv" extension used anywhere else.
</aside>

---

