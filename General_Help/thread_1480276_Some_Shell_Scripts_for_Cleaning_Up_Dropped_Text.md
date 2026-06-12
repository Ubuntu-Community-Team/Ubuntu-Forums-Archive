---
title: "Some Shell Scripts for Cleaning Up Dropped Text"
date: 2010-05-11
forum: General Help
---

### Post by NotPhil on 2010-05-11
I drag-and-drop text clippings from Firefox to the Gnome Desktop. Frequently they're riddled with illegible characters, and sometimes, I don't get around to titling the files until I have a pretty big collection of clippings.

So, I wrote a few scripts to help me manage these text clippings. Feel free to use and modify them as you like:

```

#!/bin/bash

# cleanup-chars.sh replaces most of the garbled characters in text 
# dragged from Firefox to Nautilus with their legible counterparts.

for FILENAME in *.txt*; do
    sed -i              \
        -e s/â€œ/\“/g     \
        -e s/â€/\”/g     \
        -e s/â€˜/\‘/g     \
        -e s/â€™/\’/g     \
        -e s/â€¦/.../g     \
        -e s/â€”/—/g     \
        -e s/â€“/—/g     \
        -e s/Ã‰/É/g    \
        -e s/Ã©/é/g     \
        -e s/Ã±/ñ/g     \
        -e s/Ã/à/g      \
        "$FILENAME"
done

``````

#!/bin/bash

# name-text.sh displays the first fews lines of each file named
# "dropped text.txt" in a folder and allows the user to select
# which line will become the file's name.

for DROPPEDTEXT in dropped*; do

    L1=$( sed -n 1p "$DROPPEDTEXT" )
    L2=$( sed -n 2p "$DROPPEDTEXT" )
    L3=$( sed -n 3p "$DROPPEDTEXT" )
    L4=$( sed -n 4p "$DROPPEDTEXT" )
    L5=$( sed -n 5p "$DROPPEDTEXT" )
    L6=$( sed -n 6p "$DROPPEDTEXT" )
    L7=$( sed -n 7p "$DROPPEDTEXT" )
    L8=$( sed -n 8p "$DROPPEDTEXT" )
    L9=$( sed -n 9p "$DROPPEDTEXT" )
    PS3="Select a line for the title or press [0] to skip the file: "

    select TITLE in "$L1" "$L2" "$L3" "$L4" "$L5" "$L6" "$L7" "$L8" "$L9"; do
        if [ -n "$TITLE" ]; then
            mv -u "$DROPPEDTEXT" "$TITLE.txt"
            echo
            echo $DROPPEDTEXT is now $TITLE.txt.
            echo
        else
            echo
            echo Skipping $DROPPEDTEXT.
            echo
        fi
        break
    done

done

``````

#!/bin/bash

# cleanup-names.sh replaces characters which cause problems in 
# file systems with more benign characters. Specifically, the *, 
# (, ), [, ], and " marks are removed and the :, $, &, #, %, _, 
# ?, and ! marks are replaced with (space)--, USD(space), and, 
# no.(space), (space)percent, (space), and periods. Leading, 
# trailing and double spaces should be removed, along with non- 
# printing whitespace characters. Ellipses are replaced with -- and 
# double periods are trimmed to one dot.

for FILENAME in *; do
    NEWFILENAME=$( echo "$FILENAME" | sed \
                   -e s/\*//g             \
                   -e s/\(//g             \
                   -e s/\)//g             \
                   -e s/\"//g             \
                   -e s/_/\ /g            \
                   -e s/\?/\./g           \
                   -e s/\!/\./g           \
                   -e s/'\['//g           \
                   -e s/'\]'//g           \
                   -e s/â€œ//g           \
                   -e s/â€//g           \
                   -e s/\&/and/g          \
                   -e s/\:/\ --/g         \
                   -e s/#/no\.\ /g        \
                   -e s/'\$'/USD\ /g      \
                   -e s/\%/\ percent/g    \
                   -e s/[\.][\.][\.]/--/g \
                   -e s/[\.][\.]/\./g     \
                   -e s/\\s\\s*/\ /g      \
                   -e s/^\ *//g           \
                   -e s/\ *$//g )
    mv -u "$FILENAME" "$NEWFILENAME"
done

```

Okay, it looks like the bulliten-board software is converting some of the characters to different characters, so I'll attach the actual scripts to this post too.

---

