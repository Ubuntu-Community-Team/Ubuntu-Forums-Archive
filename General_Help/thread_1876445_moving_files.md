---
title: "moving files"
date: 2011-11-06
forum: General Help
---

### Post by blackmail on 2011-11-06
Hello, I have problems moving some files, mainly from some sub-folders to another folder.

I have used photorec and recovered many files but i would like to move only the jpeg files froom those sub-folders to a single folder.

I have used:
```
ls -R | grep jpg
```
to see only those folders, but i don't know how to move those files...

The
```
mv 'ls -R | grep "jpg"' /home/pictures
```
doesn't help and i know i am doing something wrong but don't quite know what :confused:

---

### Post by apollothethird on 2011-11-06
> **blackmail said:**
> Hello, I have problems moving some files, mainly from some sub-folders to another folder.

I have used photorec and recovered many files but i would like to move only the jpeg files froom those sub-folders to a single folder.

I have used:
```
ls -R | grep jpg
```to see only those folders, but i don't know how to move those files...

The
```
mv 'ls -R | grep "jpg"' /home/pictures
```doesn't help and i know i am doing something wrong but don't quite know what :confused:

What error message are you getting?

You may be having problems with spaces in the filename.  Try placing your command into a script as such:
```

#!/bin/bash

IFSSTORE=$IFS
IFS=$(echo -en "\n\b")
mv `ls -R | grep ".pl$"` /home/pictures
IFS=$IFSSTORE

```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by blackmail on 2011-11-06
Ok so i have a directory where there are many subdirs with many types of files. I only want to list the JPG files and move them to the Pictures directory in the home folder.

Could someone tell me how this could be done?

Thank you

---

### Post by blackmail on 2011-11-06
The message i am getting is:

```
mv: cannot stat `ls -R | grep "jpg"': No such file or directory

```


but if I use only
```
ls -R | grep "jpg"
```

it works perfect,, and the files don't have spaces I think, I mean all that i have seen are without any spaces.

Also could you please explain the shell script, and what i have read so far the find command and the xargs command could be used, but i am to noob for those.

---

### Post by raja.genupula on 2011-11-06
please , Don't create multiple threads on a same issue.

---

### Post by Dimarchi on 2011-11-06
I suppose you want a way that does not require you to dabble in bash or the like? :)

Well, the simplest way to go about it is probably something like the following:

1.) Bookmark the folder you want to drag and drop the jpg files to - this being Pictures, it is already bookmarked so skip step one.
2.) Open the directory with many sub directories and click Search that you can find in the upper right of the window.
3.) Write ".jpg" (without quotes) in the search field and hit enter. Wait until the search is done.
4.) Select all, drag and drop the files to the Pictures folder.

Note that this will copy the files in question - it does not move them. For deletion there is one additional step:

5.) Select all and hit delete key. This moves files that you see in the Search result window from their respective folders to Trash.

That should do it. Probably. Maybe. Perhaps.

---

### Post by blackmail on 2011-11-06
yeah sorry, my computer stopped working and i tought that it didn't get creates especially since i could not find it...
sorry again

:(

---

### Post by blackmail on 2011-11-06
Thank you for the kind reply, i will try this version, meanwhile i have found a way to do this:

```
find /media/da1d83f5-322f-4d9c-a533-55828c81bd3e/aliette/Pictures/ -type f -name "*.jpg" -exec mv {} /home/aliette/Desktop/recuperate_sortate/sortate_imagine/jpg/ \;
```


tested and working :D

---

### Post by apollothethird on 2011-11-06
> **blackmail said:**
> The message i am getting is:

```
mv: cannot stat `ls -R | grep "jpg"': No such file or directory

```but if I use only
```
ls -R | grep "jpg"
```it works perfect,, and the files don't have spaces I think, I mean all that i have seen are without any spaces.

Also could you please explain the shell script, and what i have read so far the find command and the xargs command could be used, but i am to noob for those.

First, I meant for the ".pl$" to be ".jpg$".  I used ".pl$" because I had perl files in the directory I was testing.  I didn't have any pictures.  The dot "is to indicate there is a dot at the end.  The "$" is indicating this is the last character of the string (ie... filters "testjpeg.txt" from "test.jpg").

The "#!/bin/bash" is specifying to run the system's bash script command interpreter.

The "IFSSTORE=$IFS" and IFS="IFSSTORE" lines are saving your IFS setting and restoring it after your script finishes.  Those two lines really aren't needed.  Your settings would automatically return to normal after the script finishes.  But I include them for clarity.  It doesn't change anything in your regular environment.

The "IFS=$(echo -en "\n\b")" line changes the normal internal field separator (which is a space) to a non space character so that strings that have spaces in them are not handled as multiple strings but one string.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by blackmail on 2011-11-06
Well i did this after all by using:

```
find /media/da1d83f5-322f-4d9c-a533-55828c81bd3e/aliette/Pictures/
-type f -name "*.jpg" -exec mv {} /home/aliette/Desktop/recuperate_sortate/sortate_imagine/jpg/ \;

```

---

### Post by alarme on 2011-11-06
ls -R does not provide path

try:

find source_path -name "*.jpg" -exec mv {} destination_path \;

replace source_path and destination_path according to your needs

---

### Post by blackmail on 2011-11-06
thank you for the idea i will modify my command :)

---

### Post by oldos2er on 2011-11-06
Threads merged. Please don't start more than one thread per issue.

---

### Post by Vaphell on 2011-11-06
1) never use ls output (nor any other strings) to generate the list of files
Shell supports patterns natively and will do the job better that you
**mv *.jpg destination** works just fine and is as foolproof as it gets (it doesn't blow up when there are whitespaces or weird characters). Bash will expand that pattern for you so forget about using ls for that in a roundabout way. I repeat, forget it.
2) read #1 again
3)when there is a need for something recursive with fancy options, find command is the way to go - play with it to feel its power. Find is the swiss knife of file searching.

---

