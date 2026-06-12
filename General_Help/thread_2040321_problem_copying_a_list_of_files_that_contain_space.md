---
title: "problem copying a list of files that contain spaces"
date: 2012-08-10
forum: General Help
---

### Post by supportagent11 on 2012-08-10
I have 2 directories, one archived and one current, and would like to copy all the files that have been added to the current directory into a new directory so I can create an update disk.
Running a 'diff' command was easy enough, and now I have a text file with a list of files that need to be copied.

So, I'm running the command:
**for ITEM in $(cat files.txt); do cp -v "$ITEM" Updates; done**
However, the command is returning 'no such file or directory' for every word in the text file that is separated by a space (instead of trying to copy a file for each line of text).
I have tried replacing all the spaces in the file with "\ " but get similar results.

Is there a way I can modify my command or text file to accept spaces in the file name, or is there a way to pass the 'diff' output directly into the cp comand in the terminal so I do not have to use a text file?

---

### Post by steeldriver on 2012-08-10
try something like

```
while read item; do echo "$item"; done < files.txt
```(obviously replace the echo by whatever you want to do with $item)

btw don't use upper case names for your variables - they may overwrite environment variables

---

### Post by supportagent11 on 2012-08-10
Excellent! Exactly what I was looking for

---

