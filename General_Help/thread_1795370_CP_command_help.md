---
title: "CP command help"
date: 2011-07-02
forum: General Help
---

### Post by Headcase_Fargone on 2011-07-02
With Ubuntu I'm new to the whole Linux environment and I'm having some trouble tracking down a command that will do what I'm wanting here.  Perhaps someone here can help?
 
I have a music directory with hundreds of subdirectories, one for each album.  In each album is a "folder.jpg" file of the cover art for that specific album.  I need to make a copy of each and every one of those files named "cover.jpg" but they need to remain in the original folder that each is being copied from.  Basically I want two identical files in each folder, one named "folder.jpg" and one named "cover.jpg."
 
I'm thinking there must be a way to do this recursively with the cp command, but I'll be buggered if I can figure out what that command might be.  Copying everything recursively into one single new folder is easy enough, but that's not what I want obviously.
 
Any help?

---

### Post by mikejonesey on 2011-07-02
summin allong the lines of; 
```
find . -type f *.jpg | while read filename; do echo "I'm working on file $filename"; cp $filename `basedir $filename`cover.jpg; done
```

---

### Post by Headcase_Fargone on 2011-07-03
> **mikejonesey said:**
> summin allong the lines of; 
```
find . -type f *.jpg | while read filename; do echo "I'm working on file $filename"; cp $filename `basedir $filename`cover.jpg; done
```
 
Getting the following error:
 
find: paths must precede expression: *.jpg
 
Which part of that command do I need to replace with the path of my music folder?

---

### Post by papibe on 2011-07-03
mikejonesey's script does not work. I believe he tried to show you general ideas (use find, pipes, etc).

Here's my take. I would find all folder.jpg files, and then copy them into cover.jpg maintaining its path. This is working on my machine.

```
$ find . -type f -iname 'folder.jpg' |
while read -r filename
do
  echo -en "Found: $filename \n\t"
  cp -v "$filename" `dirname "$filename"`/cover.jpg
  echo
done
```

Hope it helps.

---

### Post by Headcase_Fargone on 2011-07-04
> **papibe said:**
> mikejonesey's script does not work. I believe he tried to show you general ideas (use find, pipes, etc).
 
Here's my take. I would find all folder.jpg files, and then copy them into cover.jpg maintaining its path. This is working on my machine.
 
```
$ find . -type f -iname 'folder.jpg' |
while read -r filename
do
  echo -en "Found: $filename \n\t"
  cp -v "$filename" `dirname "$filename"`/cover.jpg
  echo
done
```
 
Hope it helps.
 
This one gives me "'Last Word Of Folder Name' is not a directory" error when I run it.
 
For instance, if the folder is named Peter Murphy - Ninth, the error will say "'Ninth/cover.jpg' is not a directory.

---

### Post by papibe on 2011-07-04
Oops, there's spaces in your paths. I didn't consider that. This should do it:
```
find . -type f -iname 'folder.jpg' |
while read -r filename
do
  echo -en "Found: $filename \n\t"
  newfilename=`dirname "$filename"`/cover.jpg
  cp -v "$filename" "$newfilename"
  echo
done
```
Regards.

---

### Post by sisco311 on 2011-07-04
Please post an example of the directory structure.

---

### Post by sisco311 on 2011-07-04
> **papibe said:**
> Oops, there's spaces in your paths. I didn't consider that. This should do it:
```
find . -type f -iname 'folder.jpg' |
while read -r filename
do
  echo -en "Found: $filename \n\t"
  newfilename=`dirname "$filename"`/cover.jpg
  cp -v "$filename" "$newfilename"
  echo
done
```
Regards.

Hmm, if this code works, then you shouldn't use it. :evil: :)

`COMMAND` is deprecated and it isn't POSIX. One should use $(COMMAND)

In bash, instead of dirname and basename you can (and should) use Parameter Expansion:
```

dirname="${file##*/}"
filename="${file%/*}"

```

Piping find in a while loop sometimes may cause problems (not in this case). The preferred syntax is:
```
while IFS= read -d '' -r file
do
  whatever
done< <(find PATH OPTIONS -print0)

```

Even if you pipe find in while the delimiter should be the NUL byte, otherwise the script will fail with files with newlines in their names.

I would try something like:```

#!/bin/bash

cd "path/to/dir" || exit 1

shopt -s nullglob
for file in */folder.jpg
do
  **echo** cp -- "$file" "${file%/*}/cover.jpg"
done
```

My code will only show what files would have been copied. You have to delete the **echo** command to actually copy the files.

---

### Post by Headcase_Fargone on 2011-07-04
> **papibe said:**
> Oops, there's spaces in your paths. I didn't consider that. This should do it:
```
find . -type f -iname 'folder.jpg' |
while read -r filename
do
  echo -en "Found: $filename \n\t"
  newfilename=`dirname "$filename"`/cover.jpg
  cp -v "$filename" "$newfilename"
  echo
done
```
Regards.
 
This one worked wonderfully.  One of these days I'll learn to write these scripts.  Quite a bit different from VBscript.  Thanks all.

---

### Post by deconstrained on 2011-07-04
> **Headcase_Fargone said:**
> Getting the following error:
 
find: paths must precede expression: *.jpg
 
Which part of that command do I need to replace with the path of my music folder?
Try putting a trailing slash after the dot (in "find .") and enclose the expression in single quotes.

---

### Post by sisco311 on 2011-07-04
> **Headcase_Fargone said:**
> This one worked wonderfully.  One of these days I'll learn to write these scripts.  Quite a bit different from VBscript.  Thanks all.

If you want to learn bash scripting then check out the BashGuide, BashFAQ and the BashPitfalls at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/) and [http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)

---

### Post by papibe on 2011-07-04
> **Headcase_Fargone said:**
> This one worked wonderfully...
Glad you could solve it.

@sisco311, thanks for the tips, I look into them.

Regards.

---

### Post by sisco311 on 2011-07-04
> **papibe said:**
> @sisco311, thanks for the tips, I look into them.


No problem. Start with the BashPitfalls, I'm sure you will like it. ;)

---

### Post by Headcase_Fargone on 2011-07-05
> **sisco311 said:**
> If you want to learn bash scripting then check out the BashGuide, BashFAQ and the BashPitfalls at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/) and [http://wiki.bash-hackers.org/start](http://wiki.bash-hackers.org/start)
 
A solution AND reading material for homework.  Awesome.

---

