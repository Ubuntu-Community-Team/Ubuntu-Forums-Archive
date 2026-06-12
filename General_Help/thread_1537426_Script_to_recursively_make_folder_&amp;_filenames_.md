---
title: "Script to recursively make folder &amp; filenames lowercase"
date: 2010-07-23
forum: General Help
---

### Post by thomas144 on 2010-07-23
The title pretty much says what I want. I'm looking for a shell script that will recursively make all of the file and directory names in a large directory tree lowercase. It has to work with file and folder names with spaces and keep the spaces in the converted names. The reason I want to do this is because most of my personal files are on my Windows partition, and before I discovered Ubuntu, I made my file and folder names have mixed case as in "My File.txt", and now I want it to look like "my file.txt". Can anyone help me with this?

---

### Post by Vaphell on 2010-07-23
[http://www.linuxjournal.com/content/convert-filenames-lowercase](http://www.linuxjournal.com/content/convert-filenames-lowercase)

you have like 10 ways to achieve that :-)

---

### Post by thomas144 on 2010-07-23
The number of choices on that page is daunting, and I'm confused on which one to use. I need one that works on file and directory names, and works with spaces and odd characters (numbers, single quote, etc.). Do you have a recommendation on which one I should use?

---

### Post by BenAshton24 on 2010-07-23
Using find and sed:
```
find ./ | sed 's/\(.*\/\)\(.*\)/mv "\1\2" "\1\L\2"/' |sh
```

Works with folders and files and spaces and special characters and wild bears :)

---

### Post by thomas144 on 2010-07-23
I'll try running that.

---

### Post by thomas144 on 2010-07-23
It only worked partially. Everything on the first two or three branches of the directory tree is lower case, but beyond that, nothing changed. But, I ran the command repeatedly and it seems that now, all of my directory tree is lower case. I'll have to remember that command. Thanks!

---

### Post by BenAshton24 on 2010-07-23
> **thomas144 said:**
> It only worked partially. Everything on the first two or three branches of the directory tree is lower case, but beyond that, nothing changed. But, I ran the command repeatedly and it seems that now, all of my directory tree is lower case. I'll have to remember that command. Thanks!

Oh! sorry about that :S I forgot to reverse the order of the output of the find command so it basically changed the first directory and then subsequent directories didn't exist because their parents were lowercase :P

Here is the complete command :)

```
find ./ | sort -r | sed 's/\(.*\/\)\(.*\)/mv "\1\2" "\1\L\2"/' |sh
```

---

### Post by thomas144 on 2010-07-23
I'll have to remember THAT command instead. Thanks again for the help.:D My files are all lowercase now!

---

