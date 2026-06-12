---
title: "Consolidating folders into one folder on an FTP server problem"
date: 2010-11-22
forum: General Help
---

### Post by Rubi1200 on 2010-11-22
Hi,
a friend of mine has asked me for some help and I am turning to the community for some advice.

(Moderators: if it is not appropriate to post this here, please accept my apologies and remove the thread)

Here is the story in his own words:
> [FONT=PrimaSans BT,Verdana,sans-serif]We have a client which has requested that we consolidate a bunch of files 
into one folder (on the FTP server which is Linux based). I was able to 
put together this command which almost performs what I need done but not 
exactly.


find  ~/public_html/ifcddj/recordings/ -type d -not \( -name recordings \)  -print0 | xargs -0 -I {} mv "{}"<destination path>


Now here's where it gets complicated. If I run this on multiple 
directories and have all the subfolders moving to the same destination, 
there's a chance data will be overwritten in the destination directory 
if two different source folders have the same name. For example, if I 
were to move the two source directories to the destination directory, 
one "01-09-10" folder would be overwritten with another:

DESTINATION PATH => ~/public_html/ifcddj/recordings
SOURCE PATH 1 => ~/public_html/ifcddj/recordings/subfolder1/01-09-10/
SOURCE PATH 2 => ~/public_html/ifcddj/recordings/subfolder2/01-09-10/

Do you have any idea how I can overcome this?[/FONT]He told me that he tried the command already in a test and data is overwritten.

So, can the command be improved and what parameters need to be added to achieve what he wants?

Thanks in advance.

---

### Post by surfer on 2010-11-22
if two folders are the same, which one will you keep?

have you considered rsync?

---

### Post by sisco311 on 2010-11-22
[s]I would use --backup option to make a backup of each existing destination directory:
```
mv --backup=numbered dir path/to/dest
```[/s]

EDIT: Oh, I think he wants something like:
```
#!/bin/bash

#for each file in .../subfolder* do
for file in $HOME/public_html/ifcddj/recordings/*/*; do
  #if the file is a directory
  if [[ -d "${file}" ]]; then
    NEW="$HOME/public_html/ifcddj/recordings/"$(basename "${file}")""
    #if the destination directory exists
    #mv the source directory's content to it
    #otherwise mv the whole directory to the destination 
    if [[ -d "$NEW" ]]; then 
      mv -b "${file}"/* $NEW
    else
      mv "${file}" "$HOME/public_html/ifcddj/recordings/"
    fi
  fi
done

```

---

### Post by Rubi1200 on 2010-11-23
Thank you very much sisco311. I will let you know if it works out for his needs; much appreciated in any event.

---

### Post by Rubi1200 on 2010-12-05
> **sisco311 said:**
> [s]I would use --backup option to make a backup of each existing destination directory:
```
mv --backup=numbered dir path/to/dest
```[/s]

EDIT: Oh, I think he wants something like:
```
#!/bin/bash

#for each file in .../subfolder* do
for file in $HOME/public_html/ifcddj/recordings/*/*; do
  #if the file is a directory
  if [[ -d "${file}" ]]; then
    NEW="$HOME/public_html/ifcddj/recordings/"$(basename "${file}")""
    #if the destination directory exists
    #mv the source directory's content to it
    #otherwise mv the whole directory to the destination 
    if [[ -d "$NEW" ]]; then 
      mv -b "${file}"/* $NEW
    else
      mv "${file}" "$HOME/public_html/ifcddj/recordings/"
    fi
  fi
done

```
Thanks so much sisco311; that was perfect, just what he needed!!! :D

Just one little question, would it be possible to add in a line that removes/deletes the empty sub-folders once the contents have been moved?

Again, on behalf of my friend, and me too, our gratitude.

---

### Post by sisco311 on 2010-12-05
> **Rubi1200 said:**
> Thanks so much sisco311; that was perfect, just what he needed!!! :D


You're welcome!

> **Rubi1200 said:**
> 
Just one little question, would it be possible to add in a line that removes/deletes the empty sub-folders once the contents have been moved?


Yes:
```
#!/bin/bash

#for each file in .../subfolder* do
for file in $HOME/public_html/ifcddj/recordings/*/*; do
  #if the file is a directory
  if [[ -d "${file}" ]]; then
    NEW="$HOME/public_html/ifcddj/recordings/"$(basename "${file}")""
    #if the destination directory exists
    #mv the source directory's content to it
    #otherwise mv the whole directory to the destination 
    if [[ -d "$NEW" ]]; then 
      mv -b "${file}"/* $NEW
      **rmdir "${file}"**
    else
      mv "${file}" "$HOME/public_html/ifcddj/recordings/"
    fi
  fi
done
```

---

### Post by Rubi1200 on 2010-12-06
Again, many thanks sisco311 for your help.

---

### Post by sisco311 on 2010-12-06
My peasure.

---

