---
title: "ls | grep *zip?"
date: 2010-11-02
forum: General Help
---

### Post by krink on 2010-11-02
why does 
ls | grep *zip
return nothing for me in a folder containing 6-8 files ending with .zip
ls | grep *.txt/ pdf / mov / avi  all work as expected
 
and to add to the confusion, why does  
ls | grep s*zip
return everything (like grep *zip should) when in fact none of the actual files themselves have an s in the name?

---

### Post by coffeecat on 2010-11-02
Counter question: why are you trying to use grep when 'ls *zip', 'ls *mov', 'ls *txt', etc will do exactly what you want?

Besides, you are putting the wildcard in the wrong place. If you really want to grep the output of ls, you need to:

```
ls * | grep mov
```Or whatever. But the problem with that is if you've got a file called 'New_movie.mpg' it will be listed with that code. Better to use 'ls *mov'.

---

### Post by krink on 2010-11-02
Thats a good rebuttal.
ls *.zip 
is how i should have done it. If i was to use a wildcard, i think.

---

### Post by coffeecat on 2010-11-02
Another tip. :wink: You don't need to include the dot when searching for files in Linux. That's a Windows habit, but you'll see it everywhere on Linux forums. In a Windows command prompt (this goes back to ms-dos days) the dot is a separator between the filename and extension and has to be typed when using wildcards. In Linux (and Unix and MacOS) a dot is just another character. So..

In a Linux terminal:

```
ls *zip
```At a Windows/ms-dos command prompt:

```
dir *.zip
```

---

### Post by DaithiF on 2010-11-02
slightly moot point given coffeecats answers, but just to answer your questions:
> **krink said:**
> why does 
ls | grep *zip
return nothing for me in a folder containing 6-8 files ending with .zip

bash will expand *zip into whatever zip files exist in the directory, so your command actually becomes:
ls | grep a.zip b.zip c.zip 
etc., depending on whatever zip files you have.
now when you supply 2 or more argument to grep the second and later arguments are treated as files to be searched, and the first argument is the term to search for.  Any input piped into grep will be ignored.  So you end up grepping b.zip, c.zip etc for a string 'a.zip'


> 
ls | grep *.txt/ pdf / mov / avi  all work as expected
 
if you only had 1 .txt file in the directory, then this command would indeed work 'as expected' ... if there are 2 or more then you're in the same situation as above and unlikely to get the results you expect.
ls | grep a.txt

> 
and to add to the confusion, why does  
ls | grep s*zip
return everything (like grep *zip should) when in fact none of the actual files themselves have an s in the name?
Bash tries to expand s*zip but finds no files matching that pattern.  so what does it do?  it simply leaves the s*zip unchanged and you end up grepping the ls output for the term 's*zip'.  For grep this pattern means:  match 0 or more 's' characters followed by zip.  any zip file will match this pattern.  Note that for bash expansion the '*' wildcard means any characters, whereas for grep '*' means 0 or more of the preceding character... subtle difference

---

