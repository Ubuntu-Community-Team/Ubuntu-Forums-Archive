---
title: "problems with the date command"
date: 2010-03-03
forum: General Help
---

### Post by milawynsrealm on 2010-03-03
For my classes, I am trying to create an SH script to automatically create a file inside of vim. This will be my first useful script that I have written, so please go easy on me.

I am basically trying to do is to create a script that automatically creates a file with the year, date and time inside of the proper folder using vim. I tried to do this on my own, but came up with some error messages:

```
gotoDandC.sh: 5: +%Y: not found
gotoDandC.sh: 6: +%m: not found
gotoDandC.sh: 7: +%d: not found

```The contents of the script is as listed below:
```
#/usr/bin/sh
#
# This automatically sets the user up for the Design and Color lessons for the day

dYear=date +"%Y"
dMonth=date +"%m"
dDate=date +"%d"

vim ~/Documents/PPCC/Spring\ 2010/Design\ and\ Color/Class\ Notes/${dYear}_${dMonth}_${dDate}DC_ClassNotes.txt


```What am I doing wrong? All constructive comments are welcome. :D

---

### Post by gmargo on 2010-03-03
Use backticks.
```

dYear=`date +"%Y"`

```And you can put the entire pathname in double quotes, so then you don't have to bother escaping the spaces. (You might have to use $HOME instead of ~.)

---

### Post by milawynsrealm on 2010-03-04
Thanks for the help, but I somehow managed to find a solution a few hours after I posted. It is nice to know that your solution works as well, though. I instead used the following:
```
dYear=$(date +"%Y")

```I have another question though. Is there a way to add in text into the opened document inside of VIM like header information that I do not wish to type in again using the existing script that I am making?

---

### Post by gmargo on 2010-03-05
> **milawynsrealm said:**
> I have another question though. Is there a way to add in text into the opened document inside of VIM like header information that I do not wish to type in again using the existing script that I am making?

I assume you are not asking "how do I read a file into the vim buffer".  (If you are: use ":read file_headers.txt").  If you want to create a blank file with default headers, you can use something like:
```

FILE="$HOME/Documents/PPCC/Spring 2010/Design and Color/Class Notes/${dYear}_${dMonth}_${dDate}DC_ClassNotes.txt"
# add headers only if file does not exist
if [ ! -f "$FILE" ]; then
    cp file_headers.txt "$FILE"
fi
vim "$FILE"

```

---

### Post by milawynsrealm on 2010-03-10
[SOLVED]

Thanks for all your help. I've decided not to use the header adding code. There was some problems when trying to execute the new code, so I went back to the original code.

---

