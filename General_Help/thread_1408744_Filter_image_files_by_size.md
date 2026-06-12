---
title: "Filter image files by size"
date: 2010-02-16
forum: General Help
---

### Post by undecim on 2010-02-16
I need a command that will check the size (visual size, not file size) of every image in a folder and its sub folders, and make a copy (or even better, a hard link) of that file in a second directory if the image is larger than 1920x1080 pixels (in both dimensions, not just total area). Also, lots of these file names have spaces, so the command needs to be space-tolerant

I'm guessing I would need to use one of the imagemagick commands and find, but I'm not sure where to start. I'm still reading man pages, but I thought someone here might save me some time.

---

### Post by Girya on 2010-02-16
```
identify -format '%w %h\n' IMAGE.jpg 
```

will output the the size.

---

### Post by kaibob on 2010-02-16
The following shell script will do what you want. You have to have imagemagick installed, and you have to change the source and target directories. I briefly tested the script--it works with file names with spaces.

```
#!/bin/bash

find /source/directory -type f | while read file ; do
   width=$(identify -format %w "$file")
   height=$(identify -format %h "$file")
   if [ "$width" -gt 1920 -a "$height" -gt 1080 ] ; then
      cp "$file" /target/directory
   fi
done
```

---

### Post by undecim on 2010-02-16
> **kaibob said:**
> The following shell script will do what you want. You have to have imagemagick installed, and you have to change the source and target directories. I briefly tested the script--it works with file names with spaces.

```
#!/bin/bash

find /source/directory -type f | while read file ; do
   width=$(identify -format %w "$file")
   height=$(identify -format %h "$file")
   if [ "$width" -gt 1920 -a "$height" -gt 1080 ] ; then
      cp "$file" /target/directory
   fi
done
```

Looks good, but I just finished running my script. Out of habbit, I spent too much time making it relatively modular, and use as few external commands as possible (it took me more time to set it up like that than it saved when running, but I like efficiency)

~/bin/sizecheck.sh```
#!/bin/bash
if [ $# -ne 4 ]; then
        echo "Usage: $0 file minwidth minheight destination" >&2
        exit 1
fi
SIZE=`identify -format "%w %h" "$1"`
WIDTH=${SIZE% *}
HEIGHT=${SIZE#* }
if [ $WIDTH -ge $2 ] && [ $HEIGHT -ge $3 ]; then
        ln "$1" "${4%/}/${1##*/}"
fi
exit 0
```Then ran:
[s]find Pictures -iname "*.jpg" -o -iname "*.png" -exec ~/bin/sizecheck.sh "{}" 1920 1080 ~/Desktop/HD/ \;[/s]
[EDIT]
Oops, that command doesn't get jpg files... Adding proper brackets inside find works though: ```
find Pictures \( -iname "*.jpg" -o -iname "*.png" \) -exec ~/bin/sizecheck.sh "{}" 1920 1080 ~/Desktop/HD/ \;
```[/EDIT]

Worked liked a charm, and now I have a list of candidates for high quality HD wallpapers. Thank you Girya, for saving me the research time, and thanks kaibob for contributing to the topic.

---

