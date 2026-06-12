---
title: "command line renaming files"
date: 2009-11-06
forum: General Help
---

### Post by shortridge11 on 2009-11-06
I tried using krename to rename a large group of files, and somehow i renamed them where $ is the original file name to $$$.  I didn't back up the names, my mistake.  As an example, file1 is now called file1file1file1.  I have about 10k files named like that, and i was wondering if anyone knew how to rename them to a third of their length? or if there was a different way to do it.  Either in krename or just a quick script, i need some help =\

Thanks

---

### Post by jakupl on 2009-11-06
> **shortridge11 said:**
> I tried using krename to rename a large group of files, and somehow i renamed them where $ is the original file name to $$$.  I didn't back up the names, my mistake.  As an example, file1 is now called file1file1file1.  I have about 10k files named like that, and i was wondering if anyone knew how to rename them to a third of their length? or if there was a different way to do it.  Either in krename or just a quick script, i need some help =\

Thanks

This should be easy using "bulk rename" if you have a GUI.

EDIT: oh no, if the filenames are of different length, then you will need some script.

---

### Post by DaithiF on 2009-11-06
you could try something like this:
```
rename 's/^(\w+?)\1\1$/$1/' *
```

I would test it out on a handful of files first before unleashing it on the full list

---

### Post by DaithiF on 2009-11-06
actually, probably better to match any character (.) rather than \w, otherwise it won't work for filenames with periods, dashes, underscores, spaces, etc.  so:
```
rename 's/^(.+?)\1\1$/$1/' 
```

---

### Post by shortridge11 on 2009-11-06
the 2nd script seems to freeze, but the first one works fine on things without spaces, .s, etc.  How would i get it to work on files with extensions? such as .mp3

---

### Post by DaithiF on 2009-11-06
i don't think the 2nd should freeze, though its having to do a lot of work, so I'd expect it to take a while.  Does it run ok for you if you try it on a single file?

---

### Post by bgc on 2009-11-06
Also, an easier check to make sure that it does what you want it to do is to use the -n option beforehand.

---

### Post by shortridge11 on 2009-11-06
i've been testing it on a single file. with the first test, test1test1test1.mp3 stays the same. test1test1test1 goes to test1 though. With the second script, no response after 5 minutes, stopping the command shows the file unchanged. using the -n flag it shows 
```

xx@xxxxx:~/test$ rename -n 's/^(.+?)\1\1$/$1/'
reading filenames from STDIN

```
and nothing afterwards

---

### Post by CaKiwi on 2009-11-06
I think DaithiF left the * off the end of the second command 

rename 's/^(.+?)\1\1$/$1/' [COLOR="Red"]*[/COLOR]

---

### Post by shortridge11 on 2009-11-06
ahh that seems to have made it run. however, is there a way for it to disregard the .xxx at the end and leave it there?

---

### Post by CaKiwi on 2009-11-06
> **shortridge11 said:**
> ahh that seems to have made it run. however, is there a way for it to disregard the .xxx at the end and leave it there?
I am far from an expert but I would try
```

rename 's/^(.+?)\1\1(\..*)$/$1$2/' *

```

---

### Post by kaibob on 2009-11-06
I'm always looking for an opportunity to practice my rudimentary shell scripting skills and thought I would give this one a try. 

The format of the files is not clear to me. If some files have extensions and others don't, and the files with extensions are in the format file1.mp3file1.mp3file1.mp3, then the following script will work:

```
#!/bin/bash

for file in * ; do
   count="${#file}"
   newcount=$((count/3))
   cp "$file" "${file: 0:${newcount}}"
done
```

If some files have extensions and others don't, and the files with extensions are in the format file1file1file1.mp3, then the following script will work:

```
#!/bin/bash

for file in * ; do
   base="${file%.*}"
   extension="${file##*.}"
   count="${#base}"
   newcount=$((count/3))
   if [ "$base" = "$extension" ] ; then
      cp "$file" "${base: 0:${newcount}}"
   else
      cp "$file" "${base: 0:${newcount}}.${extension}"
   fi
done
```

The rename command, as suggested by DaithiF, is the way to go. I just wanted to try this with bash.

---

### Post by DaithiF on 2009-11-06
so for a file named like file1file1file1.mp3, this command will rename it to file1.mp3:
```
rename 's/^(.*?)\1\1(\..*)$/$1$2/' file1file1file1.mp3 
```

and of course 
```
rename 's/^(.*?)\1\1(\..*)$/$1$2/' *
```
to run for all files

and note that this isn't specific to .mp3 extensions, it will work for any.

---

### Post by shortridge11 on 2009-11-08
DaithiF- I tested it on a small group of test files and it worked, but when i tried it on the 10k files it didn't work.  Here is my output

```

xxx@xxxx:/media/Storage/xxxx$ rename 's/^(.*?)\1\1(\..*)$/$1$2/' *Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Unknown option: 4
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
xxx@xxxx:/media/Storage/xxxx$ sudo !!
sudo rename 's/^(.*?)\1\1(\..*)$/$1$2/' *
sudo: unable to execute /usr/bin/rename: Argument list too long
xxx@xxxx:/media/Storage/xxxx$

```

It's on a seperate partition, so i tried sudo just in case.  Does the fact that it's not working have something to do with it not being on the same partition?

---

### Post by DaithiF on 2009-11-08
with 10k files you're likely ending up with a command line thats simply too long, so best to do it one at a time, something like:
```
ls | while read filename; do rename 's/^(.*?)\1\1(\..*)$/$1$2/' "$filename"; done
```

---

### Post by shortridge11 on 2009-11-08
that seems to have done it. Thanks for your help =D

---

