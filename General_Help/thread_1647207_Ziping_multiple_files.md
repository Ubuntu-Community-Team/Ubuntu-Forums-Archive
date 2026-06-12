---
title: "Ziping multiple files"
date: 2010-12-17
forum: General Help
---

### Post by risen75 on 2010-12-17
I have a bunch of cd+G files (and the corresponding MP3's) and i want to zip them all together.. 1 CD+G and the matching MP3.  I know how to unzip everything recursively.. but i have no idea how to do the reverse... and have the zip have the same name as the files before the extensions (they're all named identically before the *.cdg and *.mp3) 

i know i can go and do this all by hand.. but i know it should just be a modification of this:

find . -name "*.zip" -exec unzip '{}' \;

but i'm not sure how to to the reverse..... 

HELP

---

### Post by amauk on 2010-12-17
```
#!/bin/bash

IFS=$'\n'
MP3S=$(find . -type f -name '*.mp3')
for MP3 in $MP3S; do
	if [ -f "${MP3%.*}.cdg" ]; then
		zip "${MP3%.*}.zip" "$MP3" "${MP3%.*}.cdg"
	fi
done
```

---

### Post by risen75 on 2010-12-17
Thanks.. but how do i implement it?

---

### Post by risen75 on 2010-12-17
Ok.. thanks for the help i figured it out! :) woohoo.. dang it takes awhile to go through 70GB worth of stuff :)

---

