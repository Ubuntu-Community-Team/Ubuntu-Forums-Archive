---
title: "copy a list of files located in a .txt file"
date: 2011-11-17
forum: General Help
---

### Post by sectshun8 on 2011-11-17
I'm trying to either make a single command, or even a short bash script that will read the contents of a text file (which lists file names one line at a time) and then copies those file into a specified directory.

It's really kicking my butt and I've been trying all sorts of commands I've Google'd and am getting nowhere... any help?

If it matters this is a new install of 11.10.

---

### Post by Vaphell on 2011-11-17
```
while read file; do echo "$file"; cp "$file" /destination/dir; done < list.txt

```

EDIT: i forgot to ask: are these files scattered or in one place?

---

### Post by nothingspecial on 2011-11-17
Something like this

```
while read line; do cp "$line" destination; done < "file.txt"
```

Edit, or you could do what Vaphell said :P

---

### Post by sectshun8 on 2011-11-17
Well the files listed in the txt file are in a single directory, and needing to be copied to another single directory.

I made a .sh file with full rights using that line of code... it returned a:
```

file.sh: command not found

```

Am I to assume that anywere it says file in that line should be replaced with the list.txt?  Or how would it know what file to look at?

---

### Post by sectshun8 on 2011-11-17
Okay, got the thing to run... however, I'm getting this with each file:
```

cp :cannot stat '904554 6872  -rw-r--r-- 1 username username filesize Oct 19 09:21 <filepath>': No such file or directory

```
Is it because it's regarding all the permissions and other info as part of the file path?

I used the command to generate my list:
```
 find <sourcepath> -mtime -35 -ls > list.txt
```

---

### Post by Vaphell on 2011-11-17
no, file is a variable

while read **X**; do ....; done **< list.txt**
while reads file line by line and puts the value in X variable. inside the loop you can do anything with that X

```
./file.sh
```
or ```
 sh file.sh
```

EDIT: i see there was an update, so my post is obsolete :-)

do you run your script in the directory the files are located in?

---

### Post by sectshun8 on 2011-11-17
> **Vaphell said:**
> 
do you run your script in the directory the files are located in?

I'm running the scripts while in /home/username  

All the files in the list are located in /home/username/Pictures

Sp for example I created my listed using:

```

find Pictures -mtime -35 -ls > list.txt

```

---

### Post by sectshun8 on 2011-11-17
Okay small update.

I modified my list making command and removed the "-ls".  Now it only lists the directories and files.  Now the script works and I only have one gripe left... it omits the directories.  It would be nice if it kept the file structure instead of lumping everything together.

---

### Post by Vaphell on 2011-11-17
you know, you could have copied those files with find command itself

```
find Pictures -mtime -35 -exec cp "{}" /dest/dir \;
```

edit: so you need something fancier

instead of /home/user/Pictures/.../.../... you need /some/dest/dir/.../.../... ?

---

### Post by sectshun8 on 2011-11-17
> **Vaphell said:**
> you know, you could have copied those files with find command itself

```
find Pictures -mtime -35 -exec cp "{}" /dest/dir \;
```edit: so you need something fancier

instead of /home/user/Pictures/.../.../... you need /some/dest/dir/.../.../... ?

Nope, I didn't know that :D

And yes, I would like /home/user/Pictures/.../.../.../ to then go to /media/DISKNAME/Pictures/.../.../.../

Only the /media/DISKNAME/Pictures exists... was hoping the copy over would then create the new directories and place the files accordingly.  But lets say I had the exact file structure already in place on the destination drive.  Shouldn't the cp of whatever is listed from /home/user/Pictures go to exactly the same place in /media/DISKNAME/Pictures?

K, that was easier than I thought, pesky little "-r".  Now it seems to do exactly what I want... thanks for all the help.

```

#!/bin/sh
while read file;
do echo "$file";
cp **-r** "$file" /media/DISKNAME/Pictures;
done < backup.txt

```

---

### Post by Vaphell on 2011-11-17
try this, tweak src and dest

```
#!/bin/bash

src=$HOME/test
dest=/tmp

echo src dir: "$src"
echo dest dir: "$dest"

while read f
do
  ff="${f/$src/$dest}"
  ddir="${ff%/*}"
  echo mkdir -p "$ddir"
  echo cp -v "$f" "$ff"
done < <( find "$src" -mtime -35 -type f )

```

mkdir and cp are merely printed to console in this script, remove echo to actually perform the operation when you make sure the output shows the result you like.
output:
```
$ ./fc.sh 
mkdir -p /tmp/abc
cp -v **/home/me/test**/abc/cr.sh **/tmp**/abc/cr.sh
mkdir -p /tmp/abc
cp -v **/home/me/test**/abc/file_list.txt **/tmp**/abc/file_list.txt
mkdir -p /tmp
cp -v **/home/me/test**/test_ls.txt **/tmp**/test_ls.txt

```

ff variable replaces the <source dir> part of path with <dest dir>, so you should get different beginning, but subsequent dirs should be there. mkdir is required because cp can't create destination dir for a file in case it doesn't exist.

---

