---
title: "app or script that finds directorys &amp; files with spaces"
date: 2010-01-04
forum: General Help
---

### Post by tmorphius on 2010-01-04
i need an application or shell script that can identify all the directories and files in a certain directory and can rename them to remove any spaces in the filenames.
anyone know of anything that can do this?

---

### Post by sisco311 on 2010-01-04
**Test the commands before you run them!!!**

```

cd path/to/dir
for file in *\ *; do 
  mv -i "${file}" "${file// /_}"
done

```


if you want to rename the files and dirs recursively, then create a script
/home/user/bin/ren:
```
#!/bin/bash

mv -i "$1" "${1// /_}"

```

and run:
```
find path/to/dir -depth -name "* *" -execdir /home/user/bin/ren "{}" \;
```

---

### Post by CaKiwi on 2010-01-04
Backup your files. 

Open a terminal and cd to the directory. Create a file, rmsp.awk, say, containing the following:
```

{
  a=$0;
  if (gsub(/ /, "\\ ",a)==0) next;
  gsub(/ /, "");
  b = "mv \"" a "\" " $0;
  print b;
  system(b)
}

```

Enter
```

ls | gawk -f rmsp.awk

```

If you want to process all child directories, use
```
 find . | gawk -f rmsp.awk
```

---

### Post by jamesisin on 2010-01-04
Just here to pay tribute to those who code.

Nice.

---

### Post by rnerwein on 2010-01-04
hi
to delete the spaces try this
cd your_directoriy

rename 's/\ * //' *

if rename try to rename a duplicate e.g. "one space" to
                                                           "one              space"  (here are more spaces) hey guys - the editor here pissed me off - it elimates the spaces in my example the "one space" in this line got more than one_space !!!!
                    will give you the message: "one              space" not renamed: "onespace already exists
                                                           you can use rename -f to force the command to overwrite the existing file - but i think you don' want this :-)!!
                                                           ciao

---

### Post by jamesisin on 2010-01-04
> **rnerwein said:**
> the editor here pissed me off - it elimates the spaces in my example

Try using code boxes:

```
\[CODE\]\[\/CODE\]
```

(Hahaha, you can ignore the slashes as that's the only way I could get the tags to appear in the code box, but those are the tags to create a code box.)

---

### Post by WorldTripping on 2010-01-04
If you want something with a GUI then 'pyrenamer' has always worked for me.

Does what you asked and a lot more.

---

### Post by sisco311 on 2010-01-04
> **jamesisin said:**
> Try using code boxes:

```
\[CODE\]\[\/CODE\]
```

(Hahaha, you can ignore the slashes as that's the only way I could get the tags to appear in the code box, but those are the tags to create a code box.)

Try using the noparse boxes:
[noparse][noparse][/noparse][/noparse]

:)
[Complete Guide to BBCode]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by sisco311 on 2010-01-04
> **WorldTripping said:**
> If you want something with a GUI then 'pyrenamer' has always worked for me.

Does what you asked and a lot more.

Yep, there are some bulk renaming tools:

[list]
[*]thunar (file manager)
[*]gprename (gtk)
[*]purrr (gtk)
[*]pyrenamer (gtk)
[*]gwenrename (qt)
[*]krename (qt)
[/list]

---

### Post by jamesisin on 2010-01-04
> **sisco311 said:**
> Try using the noparse boxes:
[noparse][noparse][/noparse][/noparse]

Even better.

---

### Post by tmorphius on 2010-01-04
> **CaKiwi said:**
> Backup your files. 

Open a terminal and cd to the directory. Create a file, rmsp.awk, say, containing the following:
```

{
  a=$0;
  if (gsub(/ /, "\\ ",a)==0) next;
  gsub(/ /, "");
  b = "mv \"" a "\" " $0;
  print b;
  system(b)
}

```Enter
```

ls | gawk -f rmsp.awk

```If you want to process all child directories, use
```
 find . | gawk -f rmsp.awk
```

i tried this on a test group of files and i got the output: ```

timmy@pheonix:~/Music/2pac/2pacGreatestHits/test$  find . | gawk -f rmsp.awk
mv "./03\ 2Pac\ Temptations.mp3" ./032PacTemptations.mp3
mv: cannot stat `./03\\ 2Pac\\ Temptations.mp3': No such file or directory
mv "./folder2/03\ 2Pac\ Temptations.mp3" ./folder2/032PacTemptations.mp3
mv: cannot stat `./folder2/03\\ 2Pac\\ Temptations.mp3': No such file or directory
mv "./folder2/04\ 2Pac\ God\ Bless\ The\ Dead.mp3" ./folder2/042PacGodBlessTheDead.mp3
mv: cannot stat `./folder2/04\\ 2Pac\\ God\\ Bless\\ The\\ Dead.mp3': No such file or directory
mv "./folder1/02\ 2Pac\ 2\ Of\ Amerikaz\ Most\ Wanted\ feat.SnoopDogg.mp3" ./folder1/022Pac2OfAmerikazMostWantedfeat.SnoopDogg.mp3
mv: cannot stat `./folder1/02\\ 2Pac\\ 2\\ Of\\ Amerikaz\\ Most\\ Wanted\\ feat.SnoopDogg.mp3': No such file or directory
mv "./04\ 2Pac\ God\ Bless\ The\ Dead.mp3" ./042PacGodBlessTheDead.mp3
mv: cannot stat `./04\\ 2Pac\\ God\\ Bless\\ The\\ Dead.mp3': No such file or directory

```
i noticed all the backslashs, so i had a look at the script and saw that it said 
```
 if (gsub(/ /, "\\ ",a)==0) next;
``` but i think it is supposed to say ```
 if (gsub(/ /, "\ ",a)==0) next;
``` so i changed that, and tried again and it works, however it got hung on one of my files that had a quotation mark in its name ```
mv "./folder2/04 2Pac' God Bless The Dead.mp3" ./folder2/042Pac'GodBlessTheDead.mp3
sh: Syntax error: Unterminated quoted string
``` it needs to be resilient to bad punctuation in file names, because alot of my songs have ****** filenames, thanks to people who NaM3 Th13R S0N6S like that <

---

### Post by CaKiwi on 2010-01-04
try setting variable b to have quotes around the output file
```

 b = "mv \"" a "\" \"" $0 "\"";

```

---

### Post by tmorphius on 2010-01-04
> **CaKiwi said:**
> try setting variable b to have quotes around the output file
```

 b = "mv \"" a "\" \"" $0 "\"";

```

cheers, that works great

---

