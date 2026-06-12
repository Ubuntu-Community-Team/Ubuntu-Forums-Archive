---
title: "combining find and grep"
date: 2010-09-17
forum: General Help
---

### Post by l3ecl on 2010-09-17
I'm looking for a specific phrase inside a .txt document. But when I type:

find -name *.txt | grep 'phrase' 

it grep looks at the results instead of looking inside the text file.  so it highlights text files called phrase.txt instead of looking inside the text file for phrase.

P.S.

i did find a solution:
find / -type f -exec grep -l "IP" {} \;

but can someone explain how -exec works?

---

### Post by inameiname on 2010-09-17
Here is the man page for 'find', which gives you info on the meaning of 'exec':

[http://linux.die.net/man/1/find](http://linux.die.net/man/1/find)


I just use the following to find a simple phrase or word:

> 
         **Find files that contain a text string**
grep -lir "text to find" *
The  -l switch outputs only the names of files in which the text occurs  (instead of each line containing the text), the -i switch ignores the  case, and the -r descends into subdirectories.
**Find files containing search terms on Ubuntu **
To  find files containing keywords, linux has a powerful command called  grep, which you can use to find the lines inside any file or a list of  files.
grep -i -n 'text to search' *
**List files containing text**
Used  to recursively search a directory for files containing a string, output  the names of the files and the line number. This will search all  regular files in for.
grep --with-filename --line-number `find -type f`




---

### Post by nothingspecial on 2010-09-17
> **l3ecl said:**
> 

but can someone explain how -exec works? 

A pipe (this line thing |) sends the output of one command into the input of the next one. In the case of your first example, the output of find is a list of files, so grep will search that list for matches.

-exec executes one (or more) commands on the files find has found. So in in your second example grep searches each file find has found......

....if you see what I mean.

---

