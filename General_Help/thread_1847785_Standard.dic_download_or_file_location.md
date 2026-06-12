---
title: "Standard.dic download or file location"
date: 2011-09-21
forum: General Help
---

### Post by F1r3st0rm on 2011-09-21
Hello, I am working on a programming project, but this falls under general help, I think. I know in Linux I should be able to access everything so I was wondering where OpenOffice keeps its standard.dic file. I'm making a spell checker and I need a file of the English language in order like this:
a
b
c
d
I assume standard.dic has its format as this. Thank you for reading.

---

### Post by patryk77 on 2011-09-21
Open the terminal and run:

sudo updatedb
locate .dic

While generally Ubuntu should keep its file database up to date, it doesn't hurt to update it manually with updatedb (though that may take some time).

Locate is the command to search for files. The following 2 commands:
man updatedb
man locate

will tell you all you need to know ;)

---

### Post by searchfgold6789 on 2011-09-21
I would check out:
[http://wordlist.sourceforge.net/](http://wordlist.sourceforge.net/)

---

