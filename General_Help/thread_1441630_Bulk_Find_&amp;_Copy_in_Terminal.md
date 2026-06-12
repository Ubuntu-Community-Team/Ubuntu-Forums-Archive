---
title: "Bulk Find &amp; Copy in Terminal"
date: 2010-03-29
forum: General Help
---

### Post by bernard.jansen on 2010-03-29
I have found KRename to be very useful for bulk find and renames; however, I'd like to do a find a ***copy***, which KRename doesn't appear to do.  (Please correct me if I'm wrong).

For example, I'd like to (case insensitively) search all subdirectories for files called "cover.jpg", "cover.gif", or "cover.png" and create a copy of these called "thumb.xxx", in the same subdirectory the original is found, with the same extension as the original.

Could someone help me with constructing the find command in the terminal for this, or otherwise suggest a gui application that can help me out?

---

### Post by darolu on 2010-03-29
If you only want to "find" files, use the find command: [http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)

To create thumnails, resize images, change its format, etc. Use Imagemagick: [http://www.imagemagick.org/](http://www.imagemagick.org/)

The tool you seem to need (thumbnails) is convert: [http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by bernard.jansen on 2010-03-29
> **darolu said:**
> If you only want to "find" files, use the find command: [http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)

To create thumnails, resize images, change its format, etc. Use Imagemagick: [http://www.imagemagick.org/](http://www.imagemagick.org/)

The tool you seem to need (thumbnails) is convert: [http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

darolu, thanks for your quick response.  The images are album cover art in my music collection, which aren't very large images at all.  I'm running [Squeezebox Server]("http://en.wikipedia.org/wiki/Squeezebox_Server"), which is reading the "cover.xxx"s, but seems like it wants to see separate "thumb.xxx" files.  I've experimented with a few one-offs, and a copy seems to work fine.  I don't think I need to actually create smaller thumbnail files, though I'm now thinking this is probably a great idea; it would increase the speed that the system works over the wireless network.

The problem is that I have hundreds of subfolders with album art images in them, and manual isn't an option.  At first glance, it doesn't look like ImageMagick "convert" works recursively.  I may then have to use the find and exec option anyway.  I'll look a bit closer.

Futher tips appreciated.

---

### Post by gmargo on 2010-03-29
Here's a bash script that finds the cover.* files and copies them to thumb.*.  It should be simple to adapt if you choose to use ImageMagick.

```

#!/bin/bash
# Using bash to use arrays and arithmetic

# Find album covers and process.

# Put pathnames of files in $NAMES[] array
declare -a NAMES
declare -i indx=0

# Change field separator to newline to avoid choking on spaces in pathnames.
OIFS=$IFS
IFS='\

'
# Find all entries in this directory.
for PATHNAME in $(find . -iname cover.jpg -o -iname cover.gif -o -iname cover.png -print)
do
    NAMES[indx++]="$PATHNAME"
done

# Switch back to normal field separator
IFS=$OIFS

echo "There are ${#NAMES[@]} entries:"
for (( indx=0 ; indx < ${#NAMES[@]} ; indx++ ))
do
    PATHNAME=${NAMES[indx]}
    #if [ -d "$PATHNAME" ]; then
    #    echo "\"$PATHNAME\" is a Directory"
    #elif [ -f "$PATHNAME" ]; then
    #    echo "\"$PATHNAME\" is a Regular File"
    #else
    #    echo "\"$PATHNAME\" is something else"
    #fi

    # Only operate on files
    if [ ! -f "$PATHNAME" ]; then
        continue
    fi

    DIR=$(dirname "$PATHNAME")
    FILE=$(basename "$PATHNAME")
    BASE=$(echo "$FILE" | sed 's/^\(.\+\)\.\([[:alpha:]]\+\)$/\1/')
    EXT=$( echo "$FILE" | sed 's/^\(.\+\)\.\([[:alpha:]]\+\)$/\2/')

    # Create filename for thumb
    THUMB="thumb.$EXT"
    THUMBPATH="$DIR/$THUMB"

    # Don't overwrite pre-existing thumb of this extension
    if [ -f "$THUMBPATH" ]; then
        continue
    fi

    # Do the actual copy
    cp -p "$PATHNAME" "$THUMBPATH"
    rc=$? ; if [ $rc -ne 0 ] ; then echo "ERROR: \"cp -p $PATHNAME $THUMBPATH\" failed rc=$rc" ; exit 2 ; fi

done


```

---

### Post by kaibob on 2010-03-29
Here's another suggestion. It was too long to be made into a one-liner that could be entered into a terminal window, so I made a shell script instead. You need to change /source/directory to whatever is appropriate. 

```
#!/bin/bash

find /source/directory -iname "cover.jpg" -o -iname "cover.png" -o -iname "cover.gif" \
   -type f 2> /dev/null | while read file ; do
   ext="${file##*.}"
   dir="${file%/*}"
   cp "$file" "${dir}/thumb.${ext}"
done
```

---

