---
title: "Bash: Automated file naming"
date: 2010-01-05
forum: General Help
---

### Post by sevenearths on 2010-01-05
I have a number of files on our server (trust me it's a lot!) that have spaces in them. I need to remove the spaces (so I can backup the files) but doing this using the mv command is tedious. Eg.
```
mv REGAN\ _DD3_9EG_NOR_694_06.pdf REGAN_DD3_9EG_NOR_694_06.pdf
```
Could I create a bash script that would grab the last file from a
```
>>>ls | grep \ <<<
```
statement and ask (with a simple question mark) what to use in replacement of the space (e.g. a simple return would close the space up). And then the script would just repeat till 'ls | grep \ ' returns nothing.

Any ideas?

---

### Post by gsmanners on 2010-01-05
rename 's/ /_/' *

See man rename for more info.

---

### Post by sevenearths on 2010-01-05
That would work if the space were only in the first part of the file names, but some of the spaces are in the end of the filename and have to be replaced with a dash '-' and the decision to do this can only be done manually unfortunately :(

---

### Post by raffaele181188 on 2010-01-05
Something similar could work?
```

DIR=/path/to/dir
for FILE in $DIR/* ; do
  # Exclude directories
  if [ -f "$FILE" ]; then
    # Check if it contains spaces [...] then
    echo "$FILE: which char should I replace all occurrences of ' ' with?"
    read REPLACEMENT
    # If it's blank default to a dash
    mv "$FILE" "${FILE// /$REPLACEMENT}"
  fi
done

```
If you have problem with spaces, look at IFS (internal field separator)

---

### Post by sevenearths on 2010-01-05
Sorry to be stupid, but what does this do?
```
mv "$FILE" "${FILE// /$REPLACEMENT}"
```

---

### Post by raffaele181188 on 2010-01-05
It renames $FILE, by replacing all instances of " " (space) with $REPLACEMENT :)
You asked for it, didn't you?

---

### Post by raffaele181188 on 2010-01-05
Here it's the final and tested version
TEST IT YOURSELF if you have any important data.
Bash scripts are tricky and can be very dangerous
```

#!/bin/bash
DIR=/home/foo/workspace/testdir
for FILE in $DIR/*[[:space:]]* ; do
  # Exclude directories
  if [ -f "$FILE" ]; then
    echo $(basename "$FILE") ": which char should I replace all occurrences of ' ' with?"
    read REPLACEMENT
    # If it's blank default to a dash
    if [ -z $REPLACEMENT ] ; then
      echo "Default to dash (-)"
      REPLACEMENT="-"
    fi
    mv "$FILE" "${FILE// /$REPLACEMENT}"
  fi
done

```

---

### Post by tuwe on 2010-01-05
rename 's/ //g' *

removes ALL spaces.

edit: try
```
rename -n 's/ $/-/; s/ //g' *
```

this will rename your file "bla fasel " to "blafasel-" and your file "bla fasel" to "blafasel".

To replace whitespace with something else, use 

```
rename -n 's/ $/-/; s/ /X/g' *
```

the result will be "blaXfasel-"

edit2: the -n switch does not rename the files, it actually only shows what would have been done.

---

### Post by sevenearths on 2010-01-06
> **raffaele181188 said:**
> Here it's the final and tested version
TEST IT YOURSELF if you have any important data.
Bash scripts are tricky and can be very dangerous
```

#!/bin/bash
DIR=/home/foo/workspace/testdir
for FILE in $DIR/*[[:space:]]* ; do
  # Exclude directories
  if [ -f "$FILE" ]; then
    echo $(basename "$FILE") ": which char should I replace all occurrences of ' ' with?"
    read REPLACEMENT
    # If it's blank default to a dash
    if [ -z $REPLACEMENT ] ; then
      echo "Default to dash (-)"
      REPLACEMENT="-"
    fi
    mv "$FILE" "${FILE// /$REPLACEMENT}"
  fi
done

```

Thanks very much :) nice 1!

---

### Post by sevenearths on 2010-01-06
> **tuwe said:**
> rename 's/ //g' *

removes ALL spaces.

edit: try
```
rename -n 's/ $/-/; s/ //g' *
```

this will rename your file "bla fasel " to "blafasel-" and your file "bla fasel" to "blafasel".

To replace whitespace with something else, use 

```
rename -n 's/ $/-/; s/ /X/g' *
```

the result will be "blaXfasel-"

edit2: the -n switch does not rename the files, it actually only shows what would have been done.

Thanks for that. I think I going to have to read up on string searches character replacements. It seams all abit complicated

---

### Post by gsmanners on 2010-01-06
For help with regular expressions, see perldoc (package: perl-doc).

---

### Post by sevenearths on 2010-01-11
> **raffaele181188 said:**
> Here it's the final and tested version
TEST IT YOURSELF if you have any important data.
Bash scripts are tricky and can be very dangerous
```

#!/bin/bash
DIR=/home/foo/workspace/testdir
for FILE in $DIR/*[[:space:]]* ; do
  # Exclude directories
  if [ -f "$FILE" ]; then
    echo $(basename "$FILE") ": which char should I replace all occurrences of ' ' with?"
    read REPLACEMENT
    # If it's blank default to a dash
    if [ -z $REPLACEMENT ] ; then
      echo "Default to dash (-)"
      REPLACEMENT="-"
    fi
    mv "$FILE" "${FILE// /$REPLACEMENT}"
  fi
done

```

Thanks for this script. It helped me rename 7,000 files in 2 days.

:\\:D/

(Now I just have to come up with something similar in php for the database)

---

