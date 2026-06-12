---
title: "Post &quot;$ touch&quot; arbitrary date correction help..."
date: 2011-01-18
forum: General Help
---

### Post by sudo_0 on 2011-01-18
After typing that title I realised how scandalous it sounded but maybe it pulled you in here... :)

> # touch -t 1225110099 newfile2
# ls -l &#8212;full-time new*

-rw-rw-r--1 bball    bball   0 Thu Nov 13 08:50:00 1997 newfile
-rw-rw-r--1 bball    bball   0 Sat Dec 25 11:00:00 1999 newfile2
ok... this is wrong... can someone fix it for me? 

i try this and it doesn't work... it says my date format is incorrect and creates the file -t

i'm trying to figure out how to change the date of a file back to an arbitrary date [meaning the date and time before i touched it :0) ]

thanks in advance








> [solved] 
after tinkering with the date format i figured it out... feelsdumbman.jpg

just so the answer is here for anyone else wondering:

$ cd Desktop                       # go to your desktop
$ touch newfile                     # create a new file named "newfile"
$ touch ls -l newfile               # shows you the new file and the date it was last touched literally
.......                                       # wait a minute so that the date and time of the newfile2 will be different
$ touch newfile2                     # create new file named "newfile2"
$ ls -l                                       # shows you both of the new files and the date and time they were last touched literally
$ touch -t 'date/time' newfile2  # date/time format example  201101180055 newfile2


make dates match as a test :)

---

