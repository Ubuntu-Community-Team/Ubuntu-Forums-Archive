---
title: "Text file manipulation"
date: 2006-02-06
forum: General Help
---

### Post by scpike on 2006-02-06
is there a command/script i can use to append the contents of numerous text files into one big one?

---

### Post by dcstar on 2006-02-06
[QUOTE=scpike]is there a command/script i can use to append the contents of numerous text files into one big one?[/QUOTE]
cat file1 file2 etc etc > big_file

---

### Post by scpike on 2006-02-06
thanks a lot, how about if i want to move all of the text files from a certain directory's many many subfolders into one folder, getting rid of the hierarchy and just having them all in the one folder.

i know u can use cp -r, but that maintains the hierarchy

---

### Post by nanotube on 2006-02-06
cd to the directory that you want to 'collapse'. then try 

  find . -type f -print0 |xargs -0 mv -f {} ./ 

this will move all the files that are found under your current directory from any subdirectories to your current directory. you can specify the target directory where you want to move by substituting the final "./" with anything you want, such as "/tmp/bunchofstuff/", for example.

---

