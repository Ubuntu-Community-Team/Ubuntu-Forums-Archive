---
title: "Some basic scripting help required...plz"
date: 2009-08-06
forum: General Help
---

### Post by mudasir on 2009-08-06
Hi,

I have a huge collection of audio songs. But the file name of each song is a bit messed up. When i read the ID3 info it is very clear, title shown is the real name of the song.

I made a small script to rename each file with its own ID3 Title Tag, but the thing is my collection is in DIR and SUBDIR. The script i made only works for single DIR

```

#!/bin/bash

#set -x

DIR=/sharing/audio

for i in `ls -1 $DIR | grep -v $0`
do
TITLE=`mp3info -p %t $i`
TRIM=`echo $TITLE | sed -e "s/ /-/g"`
mv $DIR/$i $DIR/$TRIM.mp3
mp3info -a "Mudasir" -c "Mudasir" $DIR/$TRIM.mp3
done

```I only want to know how will i be able to make this script work for files present in SUBDIR without destroying my data. I have been working on making this collection for more than 3 months.

DIR Structure is something like this

/sharing
->/A
--->/Movie name/
------->/file.mp3

->/B
--->/Movie name/
------->/file.mp3

Each alphabet contains about 200 Dirs.

Please Help me out.

---

### Post by cosine352 on 2009-08-06
If this helps ............
> ls -1R 
command will list subdirectories recursively.

---

### Post by mudasir on 2009-08-07
Hi,
 
This will not help me in the way i am looking for. Becasue it will first list the DIR's then it will list one by one DIR followed by the file names.
 
I have made a script to work this out also using
 
"find /sharing/testing -type f > filename.txt"
 
Now i am a bit confused because many of the files have ID3 Tag Title blank. Which simply renames my files to ".mp3" without any title.
 
Can any one figure this out.

---

### Post by martinbaselier on 2009-08-07
You can use find to execute a command. 

find * -exec command {} \;

{} is the filename (of each individual file). 

I'm gonna take a look at this too. My tag names are better organized than the filenames. So this could be helpful.

Edit: this is my output:
```
find * -name "*.mp3" -exec mp3info -p mv\ %f\ %n-%a-%t\\n {} \; > rename.sh
```
This will create a file with commands to rename each file to tracknumber-artist-tracktitle. 

This still needs some finetuning. It does not add the path now. 

You can easily adjust this to your own needs.

---

### Post by martinbaselier on 2009-08-07
I've taken a bit different approach: 
```

find ~/Muziek/* -name "*.mp3" -exec mp3info -p mv\ \"%F\"\ \"~/Muziek/%a/%l/%02n\ -\ %t\"\\n {} \; > rename.sh

```
~/Muziek is my music directory.

In the file rename.sh will be commands to move/rename each file to 
~/Muziek/%ARTIST/%ALBUM/%track_number - %track_title

FYI:
You need to precede every space with a \, for " it's the same.
\n is a new line. 
~ is your own directory.
%02n, makes sure each track number has two digits. 
used variables:
%a artist
%l album name
%t track title
%n track number
%F is the filename with path. 
see **man mp3info** for more info

Edit: according to the manual, only ID3 1.0 and 1.1 are supported. Any files in ID3v2 can not be read with this utility. It would be nice to have a commandline utility which can do that. Anyone got any suggestions?

---

