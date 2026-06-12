---
title: "applications-programming"
date: 2011-08-03
forum: General Help
---

### Post by itba on 2011-08-03
hi,
I just downloaded MySQL-Workbench and I see it in the folder:
```

/usr/bin

```how do I access it from my desktop without having to tie up my bash shell because the only way I can get to it right now is
```

cd /usr/bin
mysql-workbench

```and only when I close the program can I use my bash for anything else...can you please let me know how I can fix this....thx!

---

### Post by AlphaLexman on 2011-08-03
By putting an ampersand after the command, it will run the process in the background and you will still have your shell and command line.
```
mysql-workbench &
```

---

### Post by lykeion on 2011-08-03
If you've installed MySQL Workbench from [http://wb.mysql.com](http://wb.mysql.com) (and you selected Ubuntu as the platform), you should be able to launch it from Applications > Programming.

Otherwise if you wish to know how to create a laucher, I can tell you how you'd do that too.

EDIT
Another way is: ALT+F2 > mysql-workbench

---

### Post by itba on 2011-08-03
thx AlphaLexman

---

### Post by itba on 2011-08-03
yes [lykeion]("http://ubuntuforums.org/member.php?u=102981")
I would like to know  how to create a laucher   
and also, can you please let me know how do I get to Applications->Programming ...

right now, I just launched it with mysql-workbench &

---

### Post by lykeion on 2011-08-03
Which Ubuntu version are you running?
In 10.10 and previous versions you have an Applications menu at the top panel. In 11.04 and later this was replaced by a launcher on the left side.

Creating a launcher: [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

---

### Post by itba on 2011-08-03
I am using 11.04....oh this looks cool, let me try it out and will write how it goes

---

### Post by itba on 2011-08-03
cool, that works...thx!

---

