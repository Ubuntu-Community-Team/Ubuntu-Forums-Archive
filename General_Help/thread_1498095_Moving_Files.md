---
title: "Moving Files"
date: 2010-05-31
forum: General Help
---

### Post by jdbentley on 2010-05-31
I'm using Scheduled Tasks to move Desktop files to an archive folder so that the Desktop doesn't get cluttered. I use this command:

```
cd Desktop && mv ./* /home/jd/Documents/Archive
```

That works fine except for one thing. If the new files that are moving into the Archive have the same name as a file already there, the old file gets overwritten. I was wondering if there is some way to append numbers to the new file's name if a version or versions already exist. (This mostly affects screenshots that I save to the desktop.)

I know I could just save Screenshots straight to the archive, but I'm really curious about whether or not there's a way to append numbers in the command line.

---

### Post by cogier on 2010-05-31
There is the "mmv" command have a look here [http://ss64.com/bash/mmv.html]("http://ss64.com/bash/mmv.html")

---

### Post by sisco311 on 2010-05-31
Hi and welcome to the forums!

Try something like:
```
mv --backup=numbered file DEST
```

---

### Post by jdbentley on 2010-05-31
I'm not sure mmv does what I need it to do. I need to somehow check the files in the destination directory and if it finds a file with the same name as one of the files I'm trying to move then it appends a number to the file so that the old one isn't overwritten. If I used mmv it seems that I could append numbers, but then those numbers would be appended over and over each time the task runs so files would still be overwritten.

To be honest, though, I'm not completely clear on how mmv works so I might just not be understanding.

Using --backup=numbered didn't work either. It created hidden files in the destination directory that were numbered, but still overwrote the actual files.

---

### Post by sisco311 on 2010-05-31
this should do the trick:
```

#!/bin/bash

SOURCE="~/Desktop"
DEST="~/Documents/Archive"

for file in $SOURCE/*; do
  bfile="$(basename "$file")"
  if [ -e "$DEST/$bfile" ]; then
    i=1
    while [ -e "$DEST/$bfile".$i ]; do
      ((i++))
    done
    **echo** mv "$SOURCE/$bfile" "$DEST/$bfile".$i
  else
    **echo** mv "$SOURCE/$bfile" "$DEST"
  fi
done

```
remove the **echo** commands to actually move the files.

---

