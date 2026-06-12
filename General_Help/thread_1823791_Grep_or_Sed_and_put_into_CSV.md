---
title: "Grep or Sed and put into CSV"
date: 2011-08-12
forum: General Help
---

### Post by chipperuga on 2011-08-12
I'd to extract data from a log file and move those strings into a CSV.

Log File:
```

...
File = foo.bat
Date = 11/11/11
User = Foo Man
Size = 5
...

```

CSV should look like:
```

"foo.bat","11/11/11","Foo Man","5"

```

Ideas?

---

### Post by sanderd17 on 2011-08-12
Is it only one file, or do you have to do this in a script?

If it is only one file, I would just use a text editor (gedit or kate) and do a CTRL+F and replace

'File = ' by '"'
'\nDate = ' by '", "'
etc

remember: \n is a new line, \t is a tab

---

### Post by chipperuga on 2011-08-12
I'd like to create a script, as I have hundreds of log files to extract from.

---

### Post by sanderd17 on 2011-08-12
Ah, ok, than you'll best use sed indeed.

take a look here: [http://www.grymoire.com/Unix/Sed.html#uh-6](http://www.grymoire.com/Unix/Sed.html#uh-6)

You should make a bash script with some sed lines looking like

```

sed 's/File = /\"/g' <old_log >new_csv1
sed 's/\nDate = /\", \"/g' <new_csv1 >new_csv2

```

I probably made some mistakes, but a bit of trial and error should work. Be sure not to write to your original file. If you need to learn the basics of the shell, this is a good and short tutorial: [http://linuxcommand.org/](http://linuxcommand.org/)

---

