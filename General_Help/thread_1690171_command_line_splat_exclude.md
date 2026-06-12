---
title: "command line splat exclude?"
date: 2011-02-17
forum: General Help
---

### Post by bronquel on 2011-02-17
I'm wondering if i can exclude files after using a wild card.  something like:
rm * EXCLUDE log.txt
where i want to remove everything besides the file "log.txt"
ls * EXCLUDE *.txt
where i want to view anyfiles that do not have the extension ".txt"

---

### Post by sisco311 on 2011-02-18
In bash, if extglob is enabled, you can do something like:
```
echo !(log.txt)
echo !(file1.txt|file2.txt)
echo !(*.txt)

```

When you use it in a loop, you should enable nullglob:
```
shopt -s nullglob
for file in !(log.txt); do echo "$file"; done

```

and when you use it with a command, then failglog:
```
shopt -s failglob
ls !(*.txt)
``` 

See:
```
man bash | less +/extglob
```
and
```
man bash | less +/"Pathname Expansion"
```

---

### Post by Vaphell on 2011-02-18
```
ls -I*.txt
``` ignores *.txt in results
rm doesn't have such option but you can use find command to create complex searches and as a bonus you can execute commands on found items, rm in particular

example:
```
find . -maxdepth 1 -type f -iname 'l*' ! -iname '*txt' -exec echo "look what i've found! -> {}" \;
```
find is recursive and searches the whole subtree but min- and maxdepth can control depth of search.
- type f = only files
-iname 'l*' ! -iname '*txt' = case insensitive name l* but not *txt
-exec is optional part where you put commands to execute, in example i used echo to print out text with found object. {} is the name of found object. When you don't define any operation, find will print out names. 
find --help to see tons of possibilities that find offers

---

### Post by bronquel on 2011-02-18
thank you very much!

I'm struggling with using this command:
ls !(*.txt)
it does what i want (displaying everything besides the text files) but it displays every other non-text file in all the directories beneath.  

I hope that makes sense - if i have a directory named "test" and with in that directory i have a couple directories "blue" and "red" all filled with files (say txt, jpg, cpp, doc - a bunch of file types), and i issue the command "ls !(*.txt" i get all but the txt files from the parent directory "test" and the two directories below, "blue" and "red"

How do i prevent the command "ls !(*.txt)" from displaying contents of more than the current working directory? (something like "ls *.txt" will display only txt files in the current working directory)

thanks for y'alls help!

---

### Post by sisco311 on 2011-02-18
> **bronquel said:**
> thank you very much!

I'm struggling with using this command:
ls !(*.txt)
it does what i want (displaying everything besides the text files) but it displays every other non-text file in all the directories beneath.  


Well, that's not entirely true...

Before the ls command is executed, bash replaces !(*.txt) with all the non-text files; and in Linux directories are files too. 

So, if you have two files: *1.txt* and *2.jpg* and two directories: *red* and *blue*, then **ls !(*.txt)** is the equivalent of **ls 2.jpg red blue**.

Note that **ls 2.jpg red blue** lists every file from the *red* and *blue* sub-directories, including the .txt files.

If you want to print the non-text files, then use echo:
```
echo !(*.txt)
```

If you want to do something more complex, then you have use something like:
```
for file in !(*.txt); do
  if [ -f "$file" ]; then 
    echo "$file" is a regular file
  elif [ -d "$file" ]; then
    echo "$file" is a directory
  else
    echo "$file" is neither a non-regular file nor a directory
  fi
done
```

HTH

---

### Post by Habitual on 2011-02-18
Remove all but one file:

```
rm -f !(filename.ext)
```

---

### Post by bronquel on 2011-02-20
thanks y'all for the command line-foo education.

---

### Post by Habitual on 2011-02-20
bronquel:

speaking of fu...

[http://www.commandlinefu.com](http://www.commandlinefu.com)

---

