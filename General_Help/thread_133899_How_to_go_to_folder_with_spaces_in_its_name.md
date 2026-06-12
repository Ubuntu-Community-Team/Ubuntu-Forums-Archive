---
title: "How to go to folder with spaces in its name"
date: 2006-02-20
forum: General Help
---

### Post by Mishal on 2006-02-20
In the terminal, I cannot go to a directory called suppose /media/My Documents

That's because there is a gap between 'My' and 'Documents'. The moment I remove the gap, I can go there through the terminal. So what is way of navigating through to these type of folders in the terminal without changing names?

Thanks :)

---

### Post by heimo on 2006-02-21
Two ways:
```
cd "My Documents"
cd My\ Documents

```

Also it's easier if you use tab completion, start writing a command or file/dir name and hit tabulator.

---

### Post by RAOF on 2006-02-21
You can go to folders with any strange character in the name (*, ?, ',\ etc) by escaping them with a '\' character.  So, you'd go
```
cd /media/My\ Documents
```
Of course, with tab-autocompletion, you could probably also go
```
cd /media/My*<tab>*
``` and it would complete it to "My\ Documents"

---

### Post by Mishal on 2006-02-21
Thanks to both of you :)

Both the quotation method and backslash method works. But I have tried with tab before and it does not work. It simply lists the files with names beginning with 'My' rather than finishing it for me by putting 'Documents' at the end.

Anyway, at least I got my problem solved.:)

---

### Post by Mishal on 2006-02-21
Thanks to both of you :)

Both the quotation method and backslash method works. But I have tried with tab before and it does not work. It simply lists the files with names beginning with 'My' rather than finishing it for me by putting 'Documents' at the end.

Anyway, at least I got my problem solved.:)

---

### Post by spartas on 2006-02-21
It will list the names when there are more than one that begin with 'My'.  It does this because it doesn't know which one you want and there are more than one to choose.

The easiest way around this is to just put the backslash in or use double quotes.   Or you can just rename all the other folders that begin with 'My' to something else so it knows exactly which one you want to use.

---

