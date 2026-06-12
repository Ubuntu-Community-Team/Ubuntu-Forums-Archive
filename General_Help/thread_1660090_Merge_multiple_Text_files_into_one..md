---
title: "Merge multiple Text files into one."
date: 2011-01-04
forum: General Help
---

### Post by webcabbie on 2011-01-04
So I have like 4 dozen text files and I want to merge them into one. 

The text files all have different names that don't follow any pattern. They are all in the same folder. It would be nice not to have to list the file names or anything like that.. Is there a merge all command?

---

### Post by BicyclerBoy on 2011-01-04
first try from terminal

man cat

maybe try 

cd in folder

cat * > dump.text

---

### Post by sisco311 on 2011-01-04
Assuming that they are plain text files:
```
cd **path/to/dir**
cat * > **new.file**
```

EDIT:
D'oh! BicyclerBoy beat me to it. :)

---

### Post by webcabbie on 2011-01-05
Those directions really are not clear enough for me.. I should have mentioned I am a complete moron

The folder is on my desktop and lets say the folder is called moron. 

My next step is to open a terminal and than..

---

### Post by tornadof3 on 2011-01-05
open a terminal, type the following commands, pressing Enter after each line:
 
```

cd ~/Desktop/moron
cat * > new.filename
```

Where "new.filename" is the file name for all the merged files, eg "merged-text.txt"

---

### Post by sisco311 on 2011-01-05
> **webcabbie said:**
> Those directions really are not clear enough for me.. I should have mentioned I am a complete moron

The folder is on my desktop and lets say the folder is called moron. 

My next step is to open a terminal and than..

Than you have to navigate in the moron directory:
```
cd ~/Desktop/moron
```

**cd** - is the command which changes the current working directory

**~/Desktop/moron** - is the path to the directory; NOTE: Linux is case sensitive!

**~** - is a shorthand for your home directory (/home/username).

Now you have to concatenate (merge) the files:
```
cat * > newfile
```

**cat** - concatenates the files
***** - matches any files from the directory; before bash (the shell) executes the command it replaces * with the filenames from the directory

cat by default prints its output to stdin (the terminal window), so you have to use **>** to redirect the output to a file (newfile).

---

### Post by webcabbie on 2011-01-05
Either it didnt work or I have no idea where the file ended up.

---

### Post by tornadof3 on 2011-01-05
The file should be in the ~/Desktop/moron directory, i.e. the moron folder on your desktop.

---

### Post by jjz on 2012-06-30
The concatenation works really well, thanks for the hand-holding instructions on how to.

Can someone give equally dummy instructions to insert some text between the files and to make sure the merge retains all the blank lines at the beginning of the original files?

---

### Post by Elfy on 2012-06-30
If you want help with something else please start your own thread.

Closed

---

