---
title: "convert pdf script problem"
date: 2010-06-17
forum: General Help
---

### Post by Cowboybebop79 on 2010-06-17
Hi all I'm in the process of creating a script to batch process a bunch of pdf in to images with imagemagick this is what she looks like so far

```

#!/bin/bash

IFS=$'\n'

TESTARRAY=( $(find . -type f -name "*full.pdf") )

for (( i=0; i<${#TESTARRAY[@]}; i++ )); do
  (convert ${TESTARRAY[i]} bc.png);
done   

```

my problem is that the script dumps all of the finished images in the working dir of the script basically overwriting the last set created how would I modify this script to output the images to the same dir that the original pdf was in.

thanks for any help.

---

### Post by arrange on 2010-06-17
```
SOURCEDIR=/home/cowboy

find $SOURCEDIR -type f -iname '*.pdf' | while read SourceFile; do
  PNGFile="${SourceFile%.pdf}.png"
  if [[ ! -e "$PNGFile" ]]; then
    convert "$SourceFile" "$PNGFile"
  fi
done
```

---

### Post by Cowboybebop79 on 2010-06-17
> **arrange said:**
> ```
SOURCEDIR=/home/cowboy

find $SOURCEDIR -type f -iname '*.pdf' | while read SourceFile; do
  PNGFile="${SourceFile%.pdf}.png"
  if [[ ! -e "$PNGFile" ]]; then
    convert "$SourceFile" "$PNGFile"
  fi
done
```

well "arrange" rearranged my script fu the only problem I had was the images were in a directory with a space in the name :( solved buy trans to new dir and back after bit messy and very un fu but time is of the essence.

thanks arrange will add that to my script lib for later perusal

---

