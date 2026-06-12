---
title: "Help with unusual batch file naming issue please"
date: 2011-05-28
forum: General Help
---

### Post by macroshaft on 2011-05-28
Some time ago I used a terminal command to automatically rename load of zip files to 0000.zip, 0001.zip etc. Now I need to change them back.

They are karaoke tracks, contained in each zip are 2 identically named files, filename.mp3 and filename.cdg.

Can anyone think of a terminal command / script to automatically peek inside the zip, take the file name (song and artist) and then rename the zip to that filename? Otherwise it'll take me weeks as there's thousands of tracks.

Thanks

---

### Post by sisco311 on 2011-05-29
Back up your files!!!


Then try something like:
```
#!/bin/bash

warning ()
{
	echo "warning: cannot rename: ${1}"
} >&2

w2 ()
{
	echo "${@:-an error occurred}"
	echo
} >&2

shopt -s nullglob extglob

for file in +([0-9]).zip
do
	unset files
	while IFS=$'\n' read -r
	do
		files+=("$REPLY")
	done< <(zipinfo -1 "$file")

	if (( ${#files[@]} != 2 ))
	then
		warning "\`${file}'"
		w2 "the archive contains ${#files[@]} file(s)"
	elif [[ ${files[0]%.*} != ${files[1]%.*} ]]
	then
		warning "\`${file}'"
		w2 "filenames in the archive don't match"
	elif [[ ${files[0],,} != *.cdg ]] || [[ ${files[1],,} != *.mp3 ]]
	then
		warning "\`${file}'"
		w2 "no cdg or mp3 file in the archive"
	elif [[ -f "${files[0]%.*}.zip" ]]
	then
		warning "\`${file}'"
		w2 "\`${files[0]%.*}.zip' already exists"
	else
		# remove the echo command to actually rename the files
		echo mv -- "${file}" "${files[0]%.*}.zip"
	fi
done


```

---

