---
title: "How to: make a shell script to delete selected entries of a log file"
date: 2010-06-26
forum: General Help
---

### Post by jorgemarmo on 2010-06-26
Hi you all....

I have 2 external hdd in wich I have all my files.... yesterday, I have copied all the files from hdd1 to hdd2 and I want to eliminate duplicates so I used FSLint to find them, now, I have a txt file that looks like this:
```

/media/My Book/!!!MIS DOCUMENTOS/Documentos/2 sep2003-jun2009 USB/!TESIS/TESIS/TESIS CVT LABVIEW Y CODEWARRIOR/LabVIEW85RuntimeEngineFull.exe
/media/My Book/HDD_Toshiba/Borrable/Pen_Drive_4GB/Tesis/Super CD de la tesis/LabView/LabVIEW85RuntimeEngineFull.exe

```multiplied by millions of entries...

now I want to make a shell script to delete all the files/entries (read from the log file) that begin with:
```
 /media/My Book/HDD_Toshiba/****
```Since HDD_Toshiba is the folder in hdd1 (MyBook) that contains all the files from hdd2

I will apreciate any ideas, suggestions and comments.-

---

### Post by stderr on 2010-06-27
Look over this carefully because I may not be quite understanding what you want to achieve, but if I'm understanding correctly you want to read the log file, pick out the lines (each containing one file path) beginning with your string "/media/My Book/HDD_Toshiba/", leaving the log file as-is, and then remove each of the files from your filesystem.

This code obviously comes with no warranty or free lunch :)

```
#!/bin/bash

while read f ; do 
  if [[ $f =~ ^\/media\/My\ Book\/HDD_Toshiba\/* ]] ; then 
    rm -i "$f" 
  fi 
done < log_file.txt
```

I've put an -i flag (interactive) on the rm command so it prompts before removing every file. Only remove that if you're sure this is going to do exactly what you want!

Here's the same with the rm replaced with a harmless echo, so you can see what files it would remove were it run (I'd try this first):

```
while read f; do if [[ $f =~ ^\/media\/My\ Book\/HDD_Toshiba\/* ]] ; then echo "$f"; fi; done < log_file.txt
```

The regex is as follows:

"^" - start of the line
"\/media\/My\ Book\/HDD_Toshiba\/" - your path, with /'s and spaces escaped
"*" - any number of additional characters of any sort

---

### Post by jorgemarmo on 2010-06-27
thanks stderr, I made it with echo and seems to work fine!

however I found an alternative way for the while using grep

```
grep '/media/My Book/HDD_Toshiba' logfile.log | while read file; do echo "$file"; done 
```solved!

---

