---
title: "Looking for help with Bash Script to make directories from Filenames"
date: 2012-05-07
forum: General Help
---

### Post by AlexOnVinyl on 2012-05-07
Hi everyone,

So I'm trying to make a Nautilus bash script that will allow me to create a directory based off of a file's name

Example: file.gets.named.here.xxx (xxx in place of extension) - then I can highlight the file and make a directory named after it.

Pretty simple but it comes in handy for organizing my multimedia.  So if someone could provide some help for this, I'd be very thankful.  I want to get it to work in Nautilus, not just a bash script, a Nautilus script.

---

### Post by sisco311 on 2012-05-09
This should work with multiple files select:

```
#/bin/bash

for file in "$@"
do
    if [[ -f "$file" ]]
    then
        mkdir -- "${file%.*}"
    fi
done

```

---

### Post by AlexOnVinyl on 2012-05-09
> **sisco311 said:**
> This should work with multiple files select:

```
#/bin/bash

for file in "$@"
do
    if [[ -f "$file" ]]
    then
        mkdir -- "${file%.*}"
    fi
done

```

would this work for single files as well?

Upon execution of this script in Nautilus it didnt produce any folders..
Something is missing.. I wish I knew what.

---

### Post by AlexOnVinyl on 2012-05-10
Bump

---

### Post by Vaphell on 2012-05-10
> Upon **execution of this script in Nautilus** it didnt produce any folders..
Something is missing.. I wish I knew what.

some details would be nice

---

### Post by sisco311 on 2012-05-10
Check out the errors:
```

#/bin/bash

for file in "$@"
do
    if [[ -f "$file" ]]
    then
        new="${file%.*}"
        if [[ "$file" == "$new" ]]
        then
            new="$new.dir"
        fi
        mkdir -- "$new"
    fi
done > out.err.log 2>&1

```

this will create a log file (out.err.log) in the directory where the files are. Please post its content.

EDIT: Just tried it out and it works for me with 1 or more files.

I guess you also want to move the files to the newly created directory:
```

#!/bin/bash

shopt -s nullglob

for file
do
    if [[ -f "$file" ]]
    then
        new="${file%.*}"
        if [[ "$file" == "$new" ]]
        then
            new="$new.dir"
        fi
        mkdir -p -- "$new" || continue
        mv -b -S '.backup' -- "$file" "$new"
    fi
done

```

---

