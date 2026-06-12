---
title: "Search for files?"
date: 2010-12-29
forum: General Help
---

### Post by UncleMonty on 2010-12-29
What's the best software people know of for searching for files in Ubuntu?

---

### Post by ian dobson on 2010-12-29
Hi,

I just use locate from the terminal.

The database of files is updated automatically every few days. If you want to update the database just do sudo updatedb.

Regards
Ian Dobson

---

### Post by kgarbutt on 2010-12-29
I prefer to use locate from the terminal too.

---

### Post by UncleMonty on 2010-12-29
> **ian dobson said:**
> Hi,

I just use locate from the terminal.

The database of files is updated automatically every few days. If you want to update the database just do sudo updatedb.

Regards
Ian Dobson


How does that work? Can I browse? (I'm looking to round up all my word files if possible)

---

### Post by WorMzy on 2010-12-29
```
sudo updatedb
```
updates the database which locate uses.

You can then search for files with:
```
locate .doc
```
This will locate every file with ".doc" in it's name.

If you want to be more precise, you can use regular expressions:
```
locate --regex "\.doc(x)?$"
```

This will only locate files which *end* in ".doc" or ".docx".

Unfortunately, by default the locate database only stores information about files on your local partition; it deliberately avoids other partitions mounted in /media.

You can change this behaviour if you want, by editing /etc/updatedb.conf, but there's another command you can use, cunningly called "find".

find is a lot more complicated than locate, but this should work for you:

```
find / -regex ".*\.doc[x]?$"
```

It may take a long time to complete, depending on the number of files you have to search through. You will also get a few "permission denied" errors as find tries to look in folders that your user cannot access, you can ignore these errors.

Also, if you're expecting a lot of results, you may want to pipe the output to less, or direct the output to a file, like so:

```
find / -regex ".*\.doc[x]?$" | less
```
```
locate --regex "\.doc(x)?$" | less
```
```
find / -regex ".*\.doc[x]?$" > ~/findlist.txt
```
```
locate --regex "\.doc(x)?$" > ~/locatelist.txt
```

---

### Post by UncleMonty on 2010-12-29
> **WorMzy said:**
> ```
sudo updatedb
```
updates the database which locate uses.

You can then search for files with:
```
locate .doc
```
This will locate every file with ".doc" in it's name.

If you want to be more precise, you can use regular expressions:
```
locate --regex "\.doc(x)?$"
```

This will only locate files which *end* in ".doc" or ".docx".

Unfortunately, by default the locate database only stores information about files on your local partition; it deliberately avoids other partitions mounted in /media.

You can change this behaviour if you want, by editing /etc/updatedb.conf, but there's another command you can use, cunningly called "find".

find is a lot more complicated than locate, but this should work for you:

```
find / -regex ".*\.doc[x]?$"
```

It may take a long time to complete, depending on the number of files you have to search through. You will also get a few "permission denied" errors as find tries to look in folders that your user cannot access, you can ignore these errors.

Also, if you're expecting a lot of results, you may want to pipe the output to less, or direct the output to a file, like so:

```
find / -regex ".*\.doc[x]?$" | less
```
```
locate --regex "\.doc(x)?$" | less
```
```
find / -regex ".*\.doc[x]?$" > ~/findlist.txt
```
```
locate --regex "\.doc(x)?$" > ~/locatelist.txt
```




Thanks that's very helpful. Is there anyway of copying the results?

---

### Post by WorMzy on 2010-12-29
Copying to where? Redirecting the output (like I did in two of the bottom four examples) puts all the results into a file so it's easy to copy and paste from that.

But if you want to skip the file and just put the output straight into the clipboard, try this:

```
locate --regex "\.doc(x)?$" | xsel -ib
```
or
```
find / -regex ".*\.doc[x]?$" | xsel -ib
```

You may need to install xsel first (I can't remember if Ubuntu comes with it out-of-the-box or not). Install from the software centre or by running this:
```
sudo apt-get install xsel
```

---

### Post by UncleMonty on 2010-12-30
> **WorMzy said:**
> Copying to where? Redirecting the output (like I did in two of the bottom four examples) puts all the results into a file so it's easy to copy and paste from that.

But if you want to skip the file and just put the output straight into the clipboard, try this:

```
locate --regex "\.doc(x)?$" | xsel -ib
```
or
```
find / -regex ".*\.doc[x]?$" | xsel -ib
```

You may need to install xsel first (I can't remember if Ubuntu comes with it out-of-the-box or not). Install from the software centre or by running this:
```
sudo apt-get install xsel
```

Very helpful thanks. Does this work if you are looking for a word doc but only know a word in the file but not the filename?

---

### Post by daqron on 2010-12-30
> **UncleMonty said:**
> Very helpful thanks. Does this work if you are looking for a word doc but only know a word in the file but not the filename?
Have a look at [http://www.athabascau.ca/html/depts/compserv/webunit/HOWTO/find.htm#EX03](http://www.athabascau.ca/html/depts/compserv/webunit/HOWTO/find.htm#EX03). For example:
```
find . -exec grep "[COLOR="Red"]KNOWN TEXT[/COLOR]" '{}' \; -print 
```
Make sure you navigate to the closest directory you can (i.e., if the file is somewhere in your home folder, navigate there first) since that command will search the current directory and all sub-directories; if you start from root that might take a while. 

A smart person will reply and explain how to narrow that search to only ".doc" files; don't know that part off the top of my head.

---

### Post by WorMzy on 2010-12-30
daqron's command should do the trick. You can just combine the two different methods to utilise both:

```
find / -regex ".*\.doc[x]?$" -exec grep "SEARCH TERM" '{}' \; -print
```

Also, I forgot to mention that the pattern matching is case sensitive, so in my examples .DOC files won't be found. This also applies to "SEARCH TERM", as in "search term" wouldn't be matched. You can match both cases by using iregex instead of the regex flag, and setting the -i flag for the grep command:

```
find / -**iregex** ".*\.doc[x]$" -exec grep **-i** "SEARCH TERM" '{}' \; -print
```

---

### Post by UncleMonty on 2011-01-13
Thanks guys.

---

