---
title: "Replace in .txt"
date: 2009-08-15
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-15
What's Up?

OK, So i wondered if you have a text file with the lines the same.

```

http://www.google.com/
http://www.google.com/
```

Is their a way you could delete any double text? So the end result would be.

```

http://www.google.com/
```

Thanks Bye.

---

### Post by kaibob on 2009-08-15
You can use the sort command, either alone or with the uniq command. For example

```
sort -u file > newfile
```

You may also want to have a look at the following thread, which deals with a similar issue:

[http://ubuntuforums.org/showthread.php?t=1240759](http://ubuntuforums.org/showthread.php?t=1240759)

---

### Post by sblunix on 2009-08-15
well if you know what the double text may be then in gedit you can go ahead and click replace, then in the first box type: ```
http://www.google.com
http://www.google.com
``` and in the second box type just ```
http://www.google.com
``` and it will replace all times where [http://www.google.com](http://www.google.com) appears more than once.

---

### Post by Chamillionaire2 on 2009-08-15
Oops sorry i forgot to mention is their a way to do it via terminal, Thanks Kaibob ill give that ago.

---

### Post by warp99 on 2009-08-15
You can use sed:

```
 # delete duplicate, consecutive lines from a file (emulates "uniq").
 # First line in a set of duplicate lines is kept, rest are deleted.
 sed '$!N; /^\(.*\)\n\1$/!P; D'

```[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

Add -i $myfile to the end of the sed command replacing your file with the variable.

---

### Post by llamabr on 2009-08-15
Why bother with sed:

```
sort -u filewithduplications.txt > filewithoutduplications.txt
```

---

