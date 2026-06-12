---
title: "backup/restore 'places' bookmarks"
date: 2009-08-31
forum: General Help
---

### Post by morganpatrick on 2009-08-31
Hi,

all my FTP bookmarks are in 'Places' on my computer. How do I copy these to another computer?

---

### Post by jerrrys on 2009-09-01
if you know the file location (properties), just use a usb stick

---

### Post by morganpatrick on 2009-09-01
well that's part of the problem, though. I don't know where ubuntu stores its bookmarks. I can't right click on a bookmark and click 'properties' -- on right click it just loads the bookmark.

---

### Post by unutbu on 2009-09-01
Do you have a file called ~/.gtk-bookmarks?
At least in Intrepid, the bookmarks are located there.

PS. For those who are interested, you can often find out where information is stored by making a change to the system and then running
```

find ~/ -type f -mmin -1 -print
```
in a terminal. It shows you all the files in your home directory that have changed in the past minute.

---

### Post by morganpatrick on 2009-09-01
Solved! Thank you.

---

