---
title: "photo bash copy script .JPG"
date: 2010-12-18
forum: General Help
---

### Post by Allochtoon on 2010-12-18
Hi all,

I want to print my photos 'online'. Since i will print pictures on a regular basis now, i need to automatize the process. 

I have a .xls with the rows filled with the requested picture numbers:

1327
1330
1368
1369
1370
1372
1378
and so on.

Since i order hundreds of photos at once, selecting all these files by hand is quite a task. 

I need a script which reads the .xls or (converted).txt and copies the matching picture files to a given subdirectory.

What would be extra nice if the script would also copy the accompanying .RAW file (which sits in the same dir). 

I hope a script guru can help me out here

---

### Post by Crusty Old Fart on 2010-12-18
> **Allochtoon said:**
> 
...I hope a script guru can help me out here
Something like this?
```

#!/bin/bash
echo -e "\nEnter the full path to the filename that contains your picture numbers."
echo For example: /dir1/dir2/filename.txt
read -e NUMFILE
echo -e "\nEnter the full path to the directory that contains your pictures."
echo For example: /dir1/dir2/pictures
read -e SRCDIR
echo -e "\nEnter the name of the subdirectory into which your pictures will be copied."
echo For example: copies
read -e SUBNAME
echo -e "\nFinished.\n"
for i in $(cat "$NUMFILE"); do
  cp "$SRCDIR/$i".{jpg,JPG,raw,RAW} "$SRCDIR/$SUBNAME" > /dev/null 2>&1
done
exit 0

```Please post again if you have any questions or would like some changes made.

Merry Christmas,

Crusty

---

### Post by Crusty Old Fart on 2010-12-19
Much better than original post after many improvements.

---

### Post by Allochtoon on 2010-12-20
> **Crusty Old Fart said:**
> Something like this?
```

#!/bin/bash
echo -e "\nEnter the full path to the filename that contains your picture numbers."
echo For example: /dir1/dir2/filename.txt
read -e NUMFILE
echo -e "\nEnter the full path to the directory that contains your pictures."
echo For example: /dir1/dir2/pictures
read -e SRCDIR
echo -e "\nEnter the name of the subdirectory into which your pictures will be copied."
echo For example: copies
read -e SUBNAME
echo -e "\nFinished.\n"
for i in $(cat "$NUMFILE"); do
  cp "$SRCDIR/$i".{jpg,JPG,raw,RAW} "$SRCDIR/$SUBNAME" > /dev/null 2>&1
done
exit 0

```Please post again if you have any questions or would like some changes made.

Merry Christmas,

Crusty

Thank you very much it worked perfectly :)

One more request:
Would it be possible to give the total size being copied into the subdirectory?

Merry Christmas to you too!

---

### Post by Crusty Old Fart on 2010-12-20
> **Allochtoon said:**
> Thank you very much it worked perfectly :)

You're mighty welcome.

> **Allochtoon said:**
> 
One more request:
Would it be possible to give the total size being copied into the subdirectory?

Yes, but I need to get a better understanding of what you're asking:

[LIST]
[*]Do you want the size in terms of the number of files or number of bytes?
[*]Do you want to know the size ***before*** or ***after*** the files are copied to the subdirectory?
[*]If your desire is to know the size ***before*** the files are copied, do you want the option to decline the copy operation?
[/LIST]
As soon as I understand what you're asking, I'll get to work on it.

---

### Post by Allochtoon on 2010-12-21
> **Crusty Old Fart said:**
> You're mighty welcome.


Yes, but I need to get a better understanding of what you're asking:

[LIST]
[*]Do you want the size in terms of the number of files or number of bytes?
[*]Do you want to know the size ***before*** or ***after*** the files are copied to the subdirectory?
[*]If your desire is to know the size ***before*** the files are copied, do you want the option to decline the copy operation?
[/LIST]
As soon as I understand what you're asking, I'll get to work on it.

[LIST]
[*] Number of files and number of megabytes
[*] Before copying
[*] With decline option
[/LIST]

Thanks a bunch crusty :)

---

### Post by Crusty Old Fart on 2010-12-22
Allrighty. I reckon this should do it:
```

#!/bin/bash
set -e

echo -e "\nEnter the full path to the filename that contains your picture numbers."
echo For example: /dir1/dir2/filename.txt
read -e numfile

echo -e "\nEnter the full path to the directory that contains your pictures."
echo For example: /dir1/dir2/pictures
read -e srcdir

echo -e "\nEnter the name of the subdirectory into which your pictures will be copied."
echo For example: copies
read -e subname

echo -e "\nGathering file sizes."

for i in $(cat "$numfile"); do
  for j in jpg JPG raw RAW; do
    if [[ -e "$srcdir/$i.$j" ]]; then
      (( filesum = $filesum + 1 ))
      (( bytesum = $bytesum + $(stat --printf="%s" "$srcdir/$i.$j") ))
      filearray[$filesum]="$srcdir/$i.$j"
    fi
  done
done

megasum=$(printf "%1.2f" $(echo "$bytesum/1024/1024" | bc -l))

echo Number of files to be copied = $filesum
echo Number of megabytes to be copied = $megasum

echo -e "\nWould you like to copy the files? [Yes or No (No is the default)]"
read -e answer
if [[ "${answer:0:1}" != "Y" && "${answer:0:1}" != "y" ]]; then
  echo -e "\nNo files have been copied."
  echo -e "Script aborted.\n"
  exit 0
else
  echo -e "\nCopying files."
  for (( file=1 ; file <= $filesum ; file++ )); do
    echo Copying: ${filearray[$file]}
    cp "${filearray[$file]}" "$srcdir/$subname"
  done
fi

echo -e "\nFinished.\n"

exit 0

```Have fun!

---

