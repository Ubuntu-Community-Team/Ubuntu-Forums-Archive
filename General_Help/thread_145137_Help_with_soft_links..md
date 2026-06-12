---
title: "Help with soft links."
date: 2006-03-15
forum: General Help
---

### Post by DravenHavok on 2006-03-15
I'm just wondering if there's a command that I can use to view the soft links in a directory. I know I can use ls -al and see which ones are the soft links, but I was wondering if there was a ways to display only the soft links. Any help would be greatly appreciated.

---

### Post by Aine on 2006-03-15
```
ls -al | grep ">"
```

I dont know if thats the official way, but it works :)

---

### Post by DravenHavok on 2006-03-16
Wow there is a way! Thank you so much. This will make it much easier to sort things out. Thanks again!

---

### Post by nanotube on 2006-03-17
or try
```
find . -maxdepth 1 -type l
```
this will list all files of type link, within your current directory. find is a really powerful command, feel free to explore its manual for more options (by using command "man find") :).

---

### Post by nanotube on 2006-03-17
btw, aine, your way is nice, but will produce false positives if any filenames contain the character ">" in them. ;)
a more foolproof way to do this based on ls would be as follows:
```
ls -al |grep "^l"
```
that way, no false positives.

---

