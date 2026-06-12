---
title: "CLI-FU: How do sort multiple files with the same name?"
date: 2012-08-10
forum: General Help
---

### Post by blueturtl on 2012-08-10
So I've got myself a burst-camera that can shoot multiple images in just a few seconds. However the camera software is not very intuitive and stores all files in the following manner:

DCIM/Folder001...00x/001.jpg 002.jpg and so on.

When sorting my pictures on the computer I often use thumbnail view in my file manager, but now I have a thousand folders to go thru with names like 001 and 002 with pictures of identical names in them.

I worked around the issue somewhat by using jhead to rename the files according to their exif dates like so:

```
find ./DCIM/ -name "*.jpg" | xargs jhead -nIMG_%Y-%m-%d_%H-%M-%S
```

I then tried moving all the files to the same folder for sorting with

```
find ./DCIM/ -name "*.jpg" | xargs mv -t /path/folder
```

However it turns out not all files were renamed because apparently some of them lack exif data and jhead refuses to process them.

Now for the actual question:
Is there a way to copy all files in a folder structure named foo.jpeg into /path/folder so that when necessary they're renamed by maybe appending a letter or a number to the end of the old filename?

---

### Post by Vaphell on 2012-08-10
try this
```
lf=''; c=0; total=0;
while IFS=$'\t' read f p; do
  if [ "$f" = "$lf" ]; then
    ((c++)); ((total++))
    echo "! ${f%.*}($c).${f##*.}  |   $p"
  else
     c=0
     echo "  $f  |  $p";
  fi
  lf="$f"
done < <( find . -iname "*.jpg" -type f -printf "%f\t%p\n" | sort )
echo $total
```

you should be able to manage to modify it to actually copy files with proper name.

---

### Post by steeldriver on 2012-08-10
the other option I wondered about was whether you could use the file's mtime in cases where the exif data seems to be missing - something like this maybe? (DISCLAIMER : this is the first time I've tried to use the %T fields from the 'find' command) : 

```
#!/bin/bash

while read filepath path timestamp; do
    echo "mv $filepath $path/IMG_$timestamp"
done < <(find . -iregex '.*[0-9]+\.jpg' -printf "%p\t%h\t%TY-%Td-%Tm_%TH-%TM-%TS\n")
```then you could just mv them all as you originally intended - provided the mtimes are at least as unique as the exif times of course

---

### Post by Vaphell on 2012-08-10
won't that -iregex catch already renamed files?

---

### Post by steeldriver on 2012-08-10
oooh... didn't think of that, you're probably right (especially since %S seems to include decimal fractions of a second)

I also forgot to add back the .jpg suffix

How about this? or do I need to bracket the tests - I seem to recall something funny about default print actions?

```
#!/bin/bash

while read filepath path timestamp; do
    echo "mv $filepath $path/IMG_$timestamp**.jpg**"
done < <(find . **! -name '*IMG_*' -a** -iregex '.*[0-9]+\.jpg' -printf "%p\t%h\t%TY-%Td-%Tm_%TH-%TM-%TS\n")
```

---

### Post by Vaphell on 2012-08-10
matching twice is redundant, this should be enough to ignore IMG*
-iregex '.*[COLOR="Blue"]/[/COLOR][0-9]+\.jpg'

---

### Post by steeldriver on 2012-08-10
of course - thanks

I'm only just getting to grips with the regex matches and I always forget they are [I]path matches
[/I]
```
while read filepath path timestamp; do
    echo "mv $filepath $path/IMG_$timestamp"
done < <(find . -iregex '.*/[0-9]+\.jpg' -printf "%p\t%h\t%TY-%Td-%Tm_%TH-%TM-%TS\n")
```

---

### Post by Vaphell on 2012-08-10
lol yeah, that caught me few times too :)
hm, -name '[0-9]*.jpg' should work too, [0-9]* != IMG*

---

### Post by blueturtl on 2012-08-14
> **Vaphell said:**
> try this
```
lf=''; c=0; total=0;
while IFS=$'\t' read f p; do
  if [ "$f" = "$lf" ]; then
    ((c++)); ((total++))
    **mv "$p" "${f%.*}($c).${f##*.}"**
    echo "! ${f%.*}($c).${f##*.}  |   $p"
  else
     c=0
     echo "  $f  |  $p";
  fi
  lf="$f"
done < <( find . -iname "*.jpg" -type f -printf "%f\t%p\n" | sort )
echo $total
```

you should be able to manage to modify it to actually copy files with proper name.

The modification in bold is all I needed, thanks! The names themselves are not useful, but using a thumbnailing fileviewer such as Nautilus makes it easy to sort pictures to their appropriate folders - and now I can view them all at once in the same folder.

steeldriver, I'm curious about the naming method you proposed. If there's no exif date, how can I rename the files similar to those that do have it? Your script unfortunately for me doesn't seem to do anything (or then I just don't know how to apply it.

With the above all I had to do was save it and then run the script from the DCIM folder.

---

### Post by Vaphell on 2012-08-14
steeldriver's idea was that after initial renaming files that failed preserve their name. By looking for the pattern characteristic for old names you extract only files without exif - that should be done with find -iregex. Run the find command alone to see if you get any output. If not then regex is wrong or you simply have 0 matching files.

Next stage is generating the list of properties, similar to my version, but with additional timestamp which is a property of the file itself - creation/modification time (-printf <format string> where **%TY**-**%Td**-**%Tm**_**%TH**-**%TM**-**%TS** is the time).

find output would be like this:
```
./ls/ls/2.jpg	./ls/ls 	2011-30-03_19-25-07.3390610000
./ls/ls/3.jpg	./ls/ls 	2011-30-03_19-25-07.3390610000

```
tab separated list of filepath / path (dir) / timestamp

you pass that to while read filepath / path /timestamp and use these fields to generate mv command.
```
mv "$filepath" "$path/$timestamp"
``` 
only fix required would be adding the extension to the new name and possibly dropping trailing subsecond digits ( "${timestamp%.*}.jpg" )

*while **IFS=$'\t'** read ...* is required, otherwise read won't be able to parse lines into fields correctly.

Note that the timestamp may or may not be useful, because it depends on the file history. You need to check if the suggested dates make any sense. Another caveat is it's possible for files to have the same timestamp - my junk example files surely do - and you would risk overwriting files processed earlier.

---

