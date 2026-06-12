---
title: "Script NOOB needs help with a simple script"
date: 2010-06-12
forum: General Help
---

### Post by Zeedok on 2010-06-12
I am trying to write a simple little script to combine and compress scanned pdf pages into a single pdf using pdftk and gs.

I need some help tweaking my script so I can use it as a nautilus script.

Here's what I have so far:

```
#!/bin/bash

cd /home/zeedok/Desktop

pdftk *.pdf cat output combined.pdf

pdftk gs -dNOPAUSE -sDEVICE=pdfwrite -sOUTPUTFILE=compressed.pdf -dBATCH combined.pdf

gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sOutputFile=compressed.pdf combined.pdf
```

This version of my script combines any pdf files on my desktop (/zeedok) into a single pdf and uses gs to reduce the filesize.

Ideally, I would like to make a few enhancements to make it work better as a nautilus script.  I hope to be able to use nautilus to navigate to a directory, then:

1. Select the pdf files that are to be included 
2. Right click to run the script
3. Delete the "combined.pdf"

I need help to:
1. Include the current or working directory as displayed in nautilus in the script
2. Only combine the files selected in nautilus rather than all of the pdf files 

I am also not sure how to stipulate the order of the pdf files in the final.pdf

Can anyone offer a few tips??

---

### Post by Zeedok on 2010-06-12
Bump

---

### Post by Zeedok on 2010-06-13
Someone at another forum helped me out with this and although I can take no credit for the script, I thought I'd post it here in case anyone else finds it useful:

```
#!/bin/bash

 # A bit of debug to see our input
 # zenity --info --text="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
 # zenity --info --text="$NAUTILUS_SCRIPT_CURRENT_URI"
 # zenity --info --text="$NAUTILUS_SCRIPT_SELECTED_URIS"

 # Get NAUTILUS_SCRIPT_SELECTED_FILE_PATHS into an array. Input is
 # newline separated. Lets hope we dont have any filenames with
 # newlines in it :-)
OLDIFS="$IFS"
IFS=$'\n'
selected_files=($NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)
IFS="$OLD_IFS"

 # work out the output directory
nautilus_dir="${NAUTILUS_SCRIPT_CURRENT_URI/file:\/\//}"
dir=""
for file in "${selected_files[@]}" ; do
        if [ -z "$dir" ] ; then
                dir="${file%/*}"
        elif [ "$dir" != "${file%/*}" ] ; then
                dir=""
                break
        fi
done

pdftk "${selected_files[@]}" cat output - \
        | gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH \
          -sOutputFile="${dir:-$nautilus_dir}/compressed.pdf" -
```

---

