---
title: "Finding and deleting multiple files"
date: 2010-02-20
forum: General Help
---

### Post by nem515 on 2010-02-20
I'm still fairly new when it comes to scripting and the sorts, but I've run into a pretty urgent issue at work.

I know I'll need grep, xargs, rm, find(?) - but the syntax is beyond me.

I have around 50000 files. The file names are similar to:
ABC123-H
ABC123-D
ABC124-H
ABC124-D
ABCDEF-H
ABCDEF-D

I need to search through the '-H' files to see if they contain the string "abc" and if it exists, delete the file along with it's '-D' partner.

Any help would be greatly appreciated!

---

### Post by xiainx on 2010-02-20
> **nem515 said:**
> I'm still fairly new when it comes to scripting and the sorts, but I've run into a pretty urgent issue at work.

I know I'll need grep, xargs, rm, find(?) - but the syntax is beyond me.

I have around 50000 files. The file names are similar to:
ABC123-H
ABC123-D
ABC124-H
ABC124-D
ABCDEF-H
ABCDEF-D

The '-H' files contain the string "abc" I need to search for, and if it exists, delete the file along with it's '-D' partner.

Any help would be greatly appreciated!

Okay, here's what I'm thinking:
Get the ls, and pipe it to a file for searching
ls > filelist

Grep the filelist with *abc* ending in -H
grep *abc*-H$ > rmfiles

loops through these files, and remove each along with its -D partner
while read LINE; do
   hfile=$LINE
   dfile=${$LINE%\H}"D" 
    rm $hfile $dfile
done < rmfiles

let me know how that works, and if you have any questions!

edit:: oh, and then clean up after yourself!
rm rmfiles
rm filelist

---

### Post by nem515 on 2010-02-20
Thanks for that!

As I said I'm still very new to scripting and I'm guessing a simply copy/paste into an .sh will not suffice.

Any chance you could throw it into a script?

Thank you!

---

### Post by xiainx on 2010-02-20
Here's what I came up with, it passed my simple tests, and seems to work. Just substitute in the directory of your files in _DIRECTORY_OF_FILES_

```
#!/bin/bash
cd _DIRECTORY_OF_FILES_
ls > filelist
grep .*abc.*-H$ filelist > rmfiles
while read LINE; do
    hfile=$LINE
    dfile=${LINE%\H}"D"
    rm $hfile $dfile
done < rmfiles
rm filelist
rm rmfiles
```

lemme know if you have any questions about the script

---

### Post by jobix on 2010-02-20
If there is a -D file for every -H file, it can be done with the "find" command:

> find . -name "*ABC*-H" -exec rm -i {} \;
find . -name "*ABC*-D" -exec rm -i {} \;

You execute the above on the command line. find will find all files in the directory (and its subdirectories) that match the pattern *ABC*-H and feed it to the "rm" command to remove them. I put the "rm -i" so that it prompts you before deleting every file. Just for safety. If you don't want that, just get rid of the "-i".

---

### Post by kaibob on 2010-02-20
Here's another suggestion. 

```
#!/bin/bash

directory="/target/directory"

string="abc"

find "$directory" -name '*H' -type f | while read file ; do
   match=$(grep -m 1 "$string" "$file")
   [ "$match" ] && echo "$file" && echo "${file/%-H/-D}"
done
```

A few comments:

* The shell script works recursively. The find command is easily modified if this is not what you want. 

* I have used echo in the shell script for testing purposes. If the shell script appears to work properly, change echo to rm.

* I have tested this shell script with a few files, but I have no way to test it with 50,000 files. There may be some system or other constraints that could cause the shell script to malfunction with this number of files.

* I know you are aware of this, but you absolutely have to have a backup of your source files before using this shell script.

---

### Post by nem515 on 2010-02-20
I just read my initial post and it seems I haven't worded it incorrectly.

I don't want to search through the filenames, I actually want to search within the -H file for the string "abc". If the string does exist, I would like to remove the -H and the -D file.

Sorry for the mixup.

kaibob: Will your script do this?

---

### Post by kaibob on 2010-02-21
> **nem515 said:**
> I just read my initial post and it seems I haven't worded it incorrectly.

I don't want to search through the filenames, I actually want to search within the -H file for the string "abc". If the string does exist, I would like to remove the -H and the -D file.

Sorry for the mixup.

kaibob: Will your script do this?

Yes! That's what grep does.

---

### Post by jobix on 2010-02-21
Sorry I misunderstood. This will work:

> 
for i in `grep -l abc *-H | cut -d'-' -f1`
do 
  rm $i-[HD]; 
done


Of course, like kaibob said above, make sure to have a backup.

---

### Post by nem515 on 2010-02-21
> **kaibob said:**
> Here's another suggestion. 

```
#!/bin/bash

directory="/target/directory"

string="abc"

find "$directory" -name '*H' -type f | while read file ; do
   match=$(grep -m 1 "$string" "$file")
   [ "$match" ] && echo "$file" && echo "${file/%-H/-D}"
done
```

A few comments:

* The shell script works recursively. The find command is easily modified if this is not what you want. 

* I have used echo in the shell script for testing purposes. If the shell script appears to work properly, change echo to rm.

* I have tested this shell script with a few files, but I have no way to test it with 50,000 files. There may be some system or other constraints that could cause the shell script to malfunction with this number of files.

* I know you are aware of this, but you absolutely have to have a backup of your source files before using this shell script.

Just did a test run on a smaller group of files and it worked a charm.

Running on the ~50000 now and it seems to be going great, albeit taking a while.

Thank you so much, and thanks to everyone else also! :)

---

### Post by nem515 on 2010-02-21
The script just finished and worked perfect.

Thanks once again everyone :)

---

### Post by nem515 on 2010-02-23
> **kaibob said:**
> Here's another suggestion. 

```
#!/bin/bash

directory="/target/directory"

string="abc"

find "$directory" -name '*H' -type f | while read file ; do
   match=$(grep -m 1 "$string" "$file")
   [ "$match" ] && echo "$file" && echo "${file/%-H/-D}"
done
```



I'm using this script and it's working great.

I'd like to know if I could feed grep multiple strings from a file rather than creating multiple variables and using "egrep $string|$string2" which I'm currently doing.

Any ideas would be appreciated :)

---

### Post by nem515 on 2010-02-23
Re-read the man page... nevermind :)

---

