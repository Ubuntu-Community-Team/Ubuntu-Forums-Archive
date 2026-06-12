---
title: "Cannot download any files on Mozilla Firefox"
date: 2012-04-17
forum: General Help
---

### Post by thedudething on 2012-04-17
I'm using 11,10 and whenever I try to download a file using Firefox, it comes up with the normal window asking what to do with the file. Then when I choose saves and click "OK", it closes and nothing happens.

Anyone know what's wrong?

---

### Post by strask on 2012-04-18
Try going into your firefox menu, find "Downloads" and bring up the downloads list. It should have a recent history of files you have downloaded. Right-click on one and select "Open containing folder" and you should find all of your files, maybe multiple copies if you tried a bunch of times. :)

---

### Post by thedudething on 2012-04-18
Already tried, downloads window is blank

---

### Post by strask on 2012-04-18
Ouch, that doesn't sound fun. Hopefully someone else around here knows the problem; but you might try asking over at the firefox forums as well, just to cover your bases.

---

### Post by HiImTye on 2012-04-18
try opening a terminal and
```
find $HOME | grep yourdownloaded.file
```
if that doesnt work (likely because your download folder is outside your home folder) then
```
find / 2>/dev/null | grep yourdownloaded.file
```
will search every file that you have permissions to see

---

