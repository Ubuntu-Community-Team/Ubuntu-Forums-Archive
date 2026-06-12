---
title: "How to search for text string on multiple files?"
date: 2011-04-05
forum: General Help
---

### Post by ingramproductions on 2011-04-05
I have lots of php, css, and html files in my web server. Does anybody know a way to search all files and subdirectories for a specific string, such as "website title". That string might be in a file called header.php, or main.php, or whatever it might be in. Is there a way to just search for that string in all files in the web directory?

---

### Post by 1clue on 2011-04-05
find . -type f -print | sed 's/ /\\ /g' | xargs grep -i "my text string"

What that does:
Find everything in the current directory or any of its children which is a regular file.

Convert spaces in filenames to escaped spaces so the grep won't fail.

xargs converts the line-separated list of items from the find into a space separated list for the grep.

grep -i is searching while ignoring capitalization for "my text string"

---

### Post by ingramproductions on 2011-04-05
Thanks, that is exactly what i'm looking for. To bad it is such a long command though. I wish there was an easier one to remember...

---

### Post by TeoBigusGeekus on 2011-04-05
Try this
```
grep -i "my text string" -R /path/you/want/searched/
```

---

### Post by 1clue on 2011-04-05
You can create your own scripts for that sort of thing.

$HOME/bin is usually on the path for any user, mine is now but I don't know if I added it or not.  Just create the a file named the command you want, and put the command in it.  Then **chmod 700 mycommand** in it.

Before you do that though, try typing the name you want to use to see if it's already there.  You don't want to replace existing command names because it can really mess things up.

---

