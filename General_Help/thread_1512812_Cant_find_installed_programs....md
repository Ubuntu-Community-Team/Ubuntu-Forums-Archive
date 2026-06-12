---
title: "Cant find installed programs..."
date: 2010-06-18
forum: General Help
---

### Post by ubunxp on 2010-06-18
I cant find the software I´ve just installed. I installed scroung-ntfs and testdisk ...  In synaptic I get the information that the software should be put in "system > admninistration(universe).  But i CAN´T find the software there...
What does (universe) mean ?

The case is that I have a disk with windows xp - and a disk with ubuntu...

Therefor I´m trying to rescue the data on my xp-disk, having rescue-software on my ubuntu-disk.

scroung-ntfs is for trying to recover data on my broken disk

[SIZE=3]**May be it won´t work - maybe it will - but the only thing I´m interested in is HOW to find the software, so I can TRY at least... **[/SIZE]

/Ubunxp

---

### Post by colorlessprism on 2010-06-18
try pressing "ALT+F2" and in the command bar type the name of one of the programs, with any luck it will show the program below the text bar. click the program to see how it prefers to launch (i.e. thunderbird %u or gksu unetbootin). when i cannot find a program i recently installed i use this method to find the command syntax and the manually create a menu entry

---

### Post by oldos2er on 2010-06-18
"Universe" is a repository. Because testdisk is a CLI program, no GUI menu entry is created for it. I don't know what "scroung-ntfs" is but I'd wager it's also a CLI app. Run ```
sudo testdisk
``` in a terminal to start testdisk.

---

### Post by ubunxp on 2010-06-18
Thanks to the two of you

I´ll try those things now...even though I´m not so good at coding in ubuntu,.. but I´m quick learning...;-)

---

### Post by XSAlliN on 2010-06-18
What coding? :) - application based on CLI work with their specific commands (you should check their site for those, unless they're displayed by Help - as with most of them).

Coding - implies you make that application as in programing and you need to learn more then ubuntu (our linux generally speaking) for that. I'd recommend you stick with the well known branch of software, especially those with a GUI or a fronted... The biggest advantage of using CLI - is related to performance and speed, which would help if you have an ancient system, yet some are not as pleasant and practical as those with a GUI.

---

