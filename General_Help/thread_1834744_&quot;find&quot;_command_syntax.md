---
title: "&quot;find&quot; command syntax"
date: 2011-08-28
forum: General Help
---

### Post by mexjim on 2011-08-28
I've been trying to figure out how to use the "find" command to find certain files and copy them somewhere else.

I'd like to be able to search a folder and its sub folders for *.mobi files and copy those files to a different folder.

Can someone post the syntax to do this please?  Also, do all the folder names need to have no spaces?

Thanks

---

### Post by nothingspecial on 2011-08-28
```
IFS=$'\n'; find ./ -type f -name '*.mobi' -exec cp '{}' /new/folder \;
```

Will work, Sisco will probably be along in a bit to tell you the propper way to do it.

The first bit makes the seperator a new line rather than a space.

./ means the directory you are in, so you have to do it from the parent folder.

-type f means a file

-name '*.mobi' means any file ending with .mobi

-exec means do something

cp means copy

'{}' is what find has found

change /new/folder for where you want to copy them

\; exits

---

### Post by sisco311 on 2011-08-28
Hi, :)

find knows that it's dealing with file names and it splits them up nicely, so reseting the IFS is not necessary.

The -name test should always come before the -type test. We want to know if *.mobi is a file or a directory, we don't care about the type of other files.

cp accepts more files as an argument, so we can use the **-exec command '{}' +** syntax. 

cp's -b option is useful if you don't want to overwrite existing files.

```
find ./ -name '*.mobi' -type f -exec cp -b -t /path/to/dest '{}' +
```

---

### Post by Vaphell on 2011-08-28
> And here am I. 

lmao :D
"Ok guys, Sisco is here. You are not needed anymore, pick up the toys and go home."

---

### Post by nothingspecial on 2011-08-28
> **sisco311 said:**
> Hi, :)



See, told you so. :D

---

### Post by mexjim on 2011-08-28
Wow, thanks for the prompt replies.  It works well.  I'm still wondering if there's a way around searching folders and sub folders with names containing spaces.  eg "blue books" vrs "bluebooks"?  

It's a real long shot but perhaps there's a way to auto remove all spaces from folder/file names.

Thanks for the expert help.  I've been using command line for mostly simple operations and I've found the find command to be very complex!

---

### Post by nothingspecial on 2011-08-28
Well, until sisco comes back and tells you the proper way to do it :P, here are 2 solutions.

If all the files are in the same directory you can do either

```
for f in *; do mv "$f" "${f/ /}"
``` 

or ```
rename -n 's/ //g' *
```

The -n flag in the 2nd line doesn't actually rename the files, it will tell you what would happen. If you are happy with the results then run it again without -n

If the files are in multiple directories you can combine either of those 2 with find as before.

But before you try either of those, (they will work but are probably incorrect), I'd wait for sisco's corrections :)

---

### Post by Vaphell on 2011-08-28
find is powerful but not that complex. Granted, it has tons of options but in general it's all about

```
find <where> <what to look for> <optional what to do on found objects>
```

what to look for - in 95% of cases name/iname, type
what to do - usually cp/mv/rename with standard syntax

---

### Post by AlphaLexman on 2011-08-28
> **nothingspecial said:**
> Sisco will probably be along in a bit to tell you the propper way to do it.
@NothingSpecial: I feel for you, it's like every post I make, I just know sisco311 is going to correct me, or us. 

I have actually wanted to open some of my own posts with your same statement, but was afraid of the ridicule, thanks for breaking the ice so now we can all just sit and wait for sisco311 to correct us!!!!!!!!!!

**EDIT:** @sisco311 "We are not worthy!" :)

---

### Post by thi3000 on 2011-08-28
find --help

your welcome

---

### Post by BaffledMollusc on 2011-08-29
You might find this useful:

[http://arstechnica.com/open-source/news/2011/07/ask-ars-how-to-use-the-find-command-in-a-pipeline.ars](http://arstechnica.com/open-source/news/2011/07/ask-ars-how-to-use-the-find-command-in-a-pipeline.ars)

It's a nice little tutorial on what you can do with the find command.

---

### Post by sisco311 on 2011-08-29
> **nothingspecial said:**
> Well, until sisco comes back and tells you the proper way to do it :P, here are 2 solutions.

If all the files are in the same directory you can do either

```
for f in *; do mv "$f" "${f// /}"
``` 

But before you try either of those, (they will work but are probably incorrect), I'd wait for sisco's corrections :)

fixed :)

${file/ /} removes only the first space
${file// /} removes all spaces 

> **AlphaLexman said:**
> 
I have actually wanted to open some of my own posts with your same statement, but was afraid of the ridicule, thanks for breaking the ice so now we can all just sit and wait for sisco311 to correct us!!!!!!!!!!


lol

@OP

find + (perl) rename:
```
find /path/to/dir -depth -name '* *' -execdir prename -n 's/ /_/g' '{}' \;
```

We need -depth to process each directory's contents before the directory itself.

'* *' matches any file with a space in its name.

-execdir runs the command in the subdirectory containing the matched file.

This works, but it's slow because it invokes the prel script for each matched file.

find + bash:
```

#!/bin/bash


while IFS= read -r -d '' file
do
    # name of the file
    fname="${file##*/}"
    # name of the directory
    dname="${file%/*}"
    # replace the spaces in the file name
    nname="$dname/${fname// /_}"
    #rename the file
    mv -b -- "$file" "$nname"
done< <(find "**path/to/dir**" -depth -name '* *' -print0)

```

this one is much faster:
```
[sisco@acme xtmp]$ touch file\ {1..500}
[sisco@acme xtmp]$ time find ./ -depth -name '* *' -execdir prename 's/ /_/g' '{}' \;

real	0m24.125s
user	0m17.036s
sys	0m3.790s
[sisco@acme xtmp]$ rm file*
[sisco@acme xtmp]$ touch file\ {1..500}
[sisco@acme xtmp]$ time ./my_script 

real	0m1.484s
user	0m0.190s
sys	0m0.160s

```

Oh, and don't forget to backup your files ;).

---

### Post by Vaphell on 2011-08-29
yet another thread pwned by Sisco and again the citizens of Gotham City can sleep peacefully :D

---

### Post by nothingspecial on 2011-08-29
> **sisco311 said:**
> fixed :)

${file/ /} removes only the first space
${file// /} removes all spaces 




](*,)




:p

---

