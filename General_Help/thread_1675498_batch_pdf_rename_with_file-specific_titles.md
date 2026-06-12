---
title: "batch pdf rename with file-specific titles"
date: 2011-01-25
forum: General Help
---

### Post by dre12b on 2011-01-25
Can anyone give me a tip on how to script the following task?

I'm scanning in a bunch of academic articles in pdf format.  I will create a spreadsheet detailing the article author, title, and pub year for each file, along with the initial filename (001, 002, 003, etc.).  I want to run a script to rename each pdf based on the spreadsheet with something along the lines of %author%year%title.  It would be easiest to include spaces in the final filename (for the title), but if that's too tricky I can just underscore it.

---

### Post by hawkmage on 2011-01-25
There are a number of ways you could do this.  First of all I would export/save the spread sheet as text using a field separator that is not part of the field info.  If you assume that the exported text file if named scanned_info.txt you can use a loop like in this script to go though it one line at a time:
```
#!/bin/bash
exec<scanned_info.txt
while read line
do 
    echo ${line}
done
```
This script doesn't do much of anything other than read and echo each line that is read.

If the file has the existing file name in the first field and the title in the second and the year in the third you can do something like this in the loop:
```
FILE_NAME=`echo ${line} | awk '{print $1}'`
DOC_TITLE=`echo ${line} | awk '{print $2}'`
DOC_YEAR=`echo ${line} | awk '{print $3}'`
if [ -f ${FILE_NAME} ]
then
    mv ${FILE_NAME} ${DOC_TITLE}${DOC_YEAR}.pdf
else
  echo "${FILE_NAME} not found"
fi
```

You may need to play with the awk command to get it to give you the info you want.  

Also I would suggest that when you are testing don't use the "mv" command, just echo the info.

---

