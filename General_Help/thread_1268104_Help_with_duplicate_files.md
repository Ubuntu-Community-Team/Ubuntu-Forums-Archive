---
title: "Help with duplicate files"
date: 2009-09-16
forum: General Help
---

### Post by stupots on 2009-09-16
Hi,

I am an amateur photographer and have an extensive library of digital camera images that I have taken myself.  I've recently used Mediasort to import/rename my images into various folders based on the Exif metadata, so I can start to catalogue and tag them.  I've just noticed that I've somehow ended up with lots of duplicates and I don't really know how.  I've used Fslint to remove the true duplicates by filename only, but somehow I have visually duplicate images where the metadata times differ by 1 hour, so of course, I can't hash and compare.

My files are named in the format yyyymmddhhmm_<original filename>.JPG, so 200907232023_IMG_1592.JPG might have a duplicate called 200907232123_IMG_1592.JPG

Have any of the uber-geeks got an idea how I can find and remove the duplicates with Bash?!?  If there is a duplicate, it will be in the same folder and very few of my photos are taken around midnight, so your method doesn't have to deal with the date changing.

Please help, and extra kudos to anyone who can figure it out!

Thanks,
Stuart

---

### Post by StuartN on 2009-09-16
> **stupots said:**
> I have visually duplicate images where the metadata times differ by 1 hour, so of course, I can't hash and compare.

This will not solve your problem, but might help think out a solution.

Fdupes (in the repositories) will check for files with matching md5 checksums, e.g. "fdupes -r . > duplicates.txt" produces a list of almost definitely duplicates, except they must be byte-for-byte identical and different EXIF data will ruin the match.

gThumb will list duplicates, ignoring filename. I don't know of a photo application that will find identical images, ignoring differences in metadata.

---

### Post by geirha on 2009-09-16
You could try the following, which recursively find all jpegs from the current directory and print the ones that have a file with the same name, but +1 hour on the timestamp. If it looks correct, you could replace the echos inside the if with «rm "$file"», or maybe have the two files displayed, then choose whether to delete one of them.
```
#!/bin/bash

while IFS= read -d '' -r file; do
    # Split into two variables on the first underscore
    IFS=_ read timestamp name <<< "$file"

    # 8 first characters of the timestamp is the date, rest is hour&minute.
    date=${timestamp:0:8} time=${timestamp:8}

    # Use the date command to parse the date and time, add one hour, then
    # generate a timestamp with same format
    timestamp2=$(date -d "$date $time +1 hour" +%Y%m%d%H%M)

    if [[ -f ${timestamp2}_${name} ]]; then
        echo "Possible duplicates:"
        echo -e "\t$file"
        echo -e "\t${timestamp2}_${name}"
    fi
done < <(find . -iname "*_*.jpg")

```

---

### Post by DaithiF on 2009-09-16
wow, geirha's solution is pretty cool.  I wouldn't try to compete with that, but the way I was thinking was, if the suffix _IMG_1592.JPG itself is unique within that folder (ie. like an ascending sequence number assigned by your camera), then something like this:
```
find . -iname '*.jpg' | sed 's/\/[0-9]\{12\}_/\/*_/' | sort | uniq -d | while read pattern; do ls $pattern; done

```

so, strip out the datetime part of the filename, replace with a wildcard '*' that we'll use later in ls to discover the full file-names, pipe to sort and uniq -d to only show the dupes, and then pass into ls to print out the files matching the pattern.

---

### Post by stupots on 2009-09-22
Sorry for the late reply guys... I have been away for a long weekend.

Thanks for your suggestions, I'll have a play around with your solutions in the next few days and let you know how I get on ;)

Regards,
Stuart

---

