---
title: "help with listing files"
date: 2011-08-23
forum: General Help
---

### Post by babygenius55 on 2011-08-23
I'm looking for a way to use the terminal to search through a directory for a certain file type, then print what it finds, and also pass it to a file.  A txt file is good enough.  I've tried various ways with ls, find, tree, and others.  i know there is a way, but i don't know how to string the requests together.

For instance:  find ./ f -iname -R '*.exe' -print0 > my_files.txt.

I know this is all wrong, but with my very limited experience this is the best I can come up with.

---

### Post by papibe on 2011-08-23
You were very close: Try this:
```
$ find . -type f -iname '*.exe' | tee my_files.txt
```
Regards.

Edit: I missed the part you wanted both the output and the file. I'm just corrected it including Idefix82 idea below.

---

### Post by Idefix82 on 2011-08-23
You can do for example

```

find . -name \*.exe | tee output.log

```

The important thing is to escape the wildcard, so \* instead of *.

---

### Post by sisco311 on 2011-08-23
The -name test should always come before the -type test, in order to avoid having to call stat(2) on every file. 

File names should be delimited by the null character (instead of a newline). This allows file names that contain  newlines  or other  types  of white space to be correctly interpreted by the programs that process the output of find.

```
find ./ -iname '*.exe' -type f -print0 > files
```

```
while IFS= read -r -d '' file
do
    echo "$file"
done < files
```

---

### Post by babygenius55 on 2011-09-27
Thanks for the help folks.  I've looked around, and there are a whole bunch of things the people were doing that sort of worked,  I just couldn't find anything to do exactly what i wanted, the spaces in the file names were giving me poo.  I'll try you suggestions a little later.

---

