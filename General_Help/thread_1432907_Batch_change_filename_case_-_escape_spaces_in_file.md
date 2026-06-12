---
title: "Batch change filename case - escape spaces in file path"
date: 2010-03-18
forum: General Help
---

### Post by joshedmonds on 2010-03-18
I would like to recursively change the file names of all files in a directory from mixed case to lower case.

[[COLOR="Blue"]This thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=244738") proposes two bash solutions:

Single command line entry

```
for i in `find * -depth`; do (mv $i `echo $i | sed 's%[^/][^/]*$%%'``echo $i | sed 's!.*/!!' | tr [:upper:] [:lower:]`); done
```

Shell script

```
#!/bin/sh

### FUNCTIONS

# This is a recursive function
# it will enter all directories
# inside current one, and their
# subdirs aswell.
renRecursive()
{
for Item in `ls`
 do
  if [ -d $Item ]; then
   cd $Item
   renRecursive
   renFiles
   cd ..
  fi
 done
}

# This will do the actual renaming
# of the files and directories
renFiles()
{
for File in `ls`
 do
  if [ -f $File -o -d $File ]; then
   convert=`echo $File | tr [:upper:] [:lower:]`

   # Do not overwrite existing files
   # this also prevents directories from
   # being moved if there is a lowercase equivalent
   if [ $convert != $File -a ! -f $convert -a ! -d $convert ]; then
    mv $File $convert
   fi
  fi
 done
}

### MAIN SCRIPT
# (pretty simple, eh? ;)

renRecursive
renFiles

exit 0
```

Unfortunately neither of these scripts will escape spaces in the file path (directory names with spaces).

Does anyone know how either of these solutions could be changed, or another method of achieving this result (without me manually changing the directory names). Bash is preferable, but not necessary.

---

### Post by slakkie on 2010-03-18
Have a look at the rename command:

rename 'y/A-Z/a-z/' $files
rename 's/\s+/_/' $files

first, we make everything lower case, then replace the whitespace to _.

use -n to see what it does without actually doing it.

man rename for more info.

---

### Post by joshedmonds on 2010-03-18
Thanks. [[COLOR="Blue"]This link[/COLOR]]("http://www.evolt.org/renaming_files_with_perl") was helpful for crafting perl expressions that work with rename.

As was [[COLOR="Blue"]this one[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1073692").

As was [[COLOR="Blue"]this one[/COLOR]]("http://www.regular-expressions.info/quickstart.html").

---

