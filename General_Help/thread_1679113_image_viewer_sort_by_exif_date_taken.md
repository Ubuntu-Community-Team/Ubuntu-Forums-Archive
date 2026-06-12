---
title: "image viewer sort by exif date taken"
date: 2011-01-31
forum: General Help
---

### Post by bric on 2011-01-31
I've tried what feels like at least a dozen different image viewers and I'm still hunting for one that handles viewing by date taken.

The trick is that I'd like to just click the jpeg as they come off the camera and then browse through all the photos in the order taken... without having to load them into a photo management application, sort them in their, then start viewing from there.  Too many extra steps for too many pictures when you're looking at a collection that is already organized (using the file system, i.e., nested directories) back to 2000.

I need (ideally) a viewer where I click the jpeg, then go next next next through them in the order in which they were taken.

Does anyone know if this sort of thing exists?

---

### Post by gordintoronto on 2011-01-31
Both my cameras assign filenames in the order the pictures are taken. My default viewer is Eye of Gnome, which presents the pictures in order by filename.

I'm like you: I organize my pictures in folders.

---

### Post by bric on 2011-01-31
> **gordintoronto said:**
> Both my cameras assign filenames in the order the pictures are taken. My default viewer is Eye of Gnome, which presents the pictures in order by filename.

I'm like you: I organize my pictures in folders.

Unfortunately, once you accumulate enough photos (over enough years, cameras, memory cards, mem card formattings) then you can get multiplication of numbers.  Also, with several different cameras it's nice to have the pictures automatically group by date rather than filename since we have DSC0000.jpg DSCF0000.jpg IMG0000.jpg and also from another couple cameras...  

Anyway, ordered by filename is ... not what I'd prefer.  Lately I've resorted towards a 'best of the decade' ... which still leaves me around 1500 or so that I'd like to be able to browse in date taken.

---

### Post by Vaphell on 2011-01-31
can't you rename pictures to to their exif date? at least in the scope of a single folder you are guaranteed to have pictures in order and you can mass-rename rather easily with a script. You could also sort them by exif and then rename to some arbitrary naming format that would preserve that order.

EDIT: just for kicks i cooked up a demo script that generates a list of .jpg files in the 'Pictures' folder (subfolders included) that have valid exif data. At the end it sorts that temporary file by date column and shows 2 exemplary alternatives to file names. It doesn't do anything to the actual jpg files, only prints text, so there is no risk of damage.
```

#!/bin/bash

path="$HOME/Pictures"

cd "$path"
find . -iname '*.jpg' | while read file
do
  #  exif -t 0x9003 = 'Date (original)'
  exif_time=$( exif -t 0x9003 "$file" | grep -oP '\d{4}:\d{2}:\d{2} \d{2}:\d{2}:\d{2}' )
  status=$?
  if [ "$status" == "0" ]  # skip files with no exif data/no date field
  then
    echo "$file|$exif_time"
  fi 
done > pics_list.txt       # write file/exif_time to file

i=0
sort -t'|' -k2 pics_list.txt | while read line
do
  i=$((i+1))
  file=$( echo $line | awk 'BEGIN { FS="|" }; { print $1 }' )
  time=$( echo $line | awk 'BEGIN { FS="|" }; { print $2 }' )
  echo $file '=>' img_$( printf "%06g" $i ).jpg "(#$i)" '||' img_$( echo $time | sed 's/[^0-9]//g').jpg "($time)"
done

```
requires exif package to be able to read exif info from jpgs
method with order number is more robust, with dates alone there is a risk of collision between files with identical timestamps.

---

### Post by bric on 2011-02-01
> **Vaphell said:**
> can't you rename pictures to to their exif date?

I had actually considered that ... but it was beyond the scope of my experience.

And of course, 'I have windows software that offers the feature'. So I asked the question.

Thanks very much for the script.  I think I'll see if I can just append the exif date to the beginning of the files (this should allow for duplicate exif data within my tolerance for error).

And recursively running the command through the subfolders will take care of what otherwise would have been very laborious in my case.

---

### Post by Vaphell on 2011-02-01
create some dummy data set with subdirectories and few pictures in them and use it as a testing ground (modify path variable to point to it)

```

#!/bin/bash

path="$HOME/test/test"

cd "$path"
find . -type f -iname '*.jpg' | while read file
do
  #  exif -t 0x9003 = 'Date (original)'
  exif_time=$( exif -t 0x9003 "$file" 2>/dev/null | grep -oP '\d{4}.\d{2}.\d{2} \d{2}.\d{2}.\d{2}' )
  status=$?
  if [ "$status" == "0" ]  # skip files with no exif data/no date field
  then
    echo "$file" "$exif_time"
    oldname="${file##*/}"
    prefix=$( echo "$exif_time" | sed -e 's/://g' -e 's/ /_/g' )_
    other_prefix="${prefix:0:13}_"
    newname1="${prefix}${oldname}"
    newname2="${other_prefix}${oldname}"
    echo "$oldname" '->' "$newname1" '||' "$newname2" # prints example names
    # mv -Tv "$file" "$newname1" # commented, uncomment by removing #
  fi 
done

```
i'll explain key concepts i used so you can approach customization with greater understanding.
exif_time is time in 0000:00:00 00:00:00 format, extracted from the exif -t output
If the exif for a given file was successful (zero status) then script enters the 'then' part where the actual stuff happens.

oldname holds a file name without the path
prefix variable will be later glued with old name. It is derived from exif time, sed part replaces ':' with nothing (in other words deletes) and space with underscore (output format 00000000_000000_ in my example). If you got different concept, feel free to change it.
other_prefix is an alternative example you can use - it takes the value of prefix and takes only first 13 chars, starting at 0 position. Result is 00000000_0000_ - seconds are no more. Other prefix doesn't really do anything, it's only to show different option.
newname1 and 2 are examples of new names = prefix+oldname, newname1 is actually used in mv command.

mv renames the file using the value of newname variable. It is commented currently, so you can play with names without changes in file name (echo line above mv prints calculated suggestions). When you are ready, uncomment it by removing # in front of mv. Make sure you test it right on a dummy data set because cleaning up the mess if something goes wrong with mass-move/rename is not pleasant. For obvious reasons you can run it only once in current form on non-testing data - each execution adds timestamp to the name (though it's quite trivial to add some failsafe mechanics to ignore files that have date in their names already, unfortunately i was somewhat lazy ;-))

If you want to do something fancier with the format of prefix or you need some exceptions to renaming or whatever, just ask.

---

### Post by bric on 2011-02-02
This is greatly appreciated.  I will definitely be putting it to use (though perhaps not for a week or so ... to much happening in the real world right now).

Thanks again for the help!

---

