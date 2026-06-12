---
title: "Shell Script"
date: 2010-03-30
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2010-03-30
I set a variable for input from a command to go into another command but the output of command A doesn't put single quotes around the output so command B replies file not found.

Dir= /home/sin/My Files

output= /home/sin/My does not exist

Anybody know what I'm missing?

---

### Post by kerry_s on 2010-03-30
Dir="/home/sin/My Files"
or
Dir=/home/sin/My\ Files

---

### Post by blur xc on 2010-03-30
> **kerry_s said:**
> Dir="/home/sin/My Files"
or
Dir=/home/sin/My\ Files

imho- quotes work better in scripts than backslashes.  Example-
```
file="/home/john/my file"
destination="/home/jane/stupid files/"
cp "$file" "$destination"
```although I would imagine 
```
file=/home/john/my\ file
destination=/home/jane/stupid\ files/
cp "$file" "$destination"
```would work as well...  I just like keeping it consistent.

BM

---

### Post by quadproc on 2010-03-30
> **Sin@Sin-Sacrifice said:**
> I set a variable for input from a command to go into another command but the output of command A doesn't put single quotes around the output so command B replies file not found.

Dir= /home/sin/My Files

As other posters have implied, the problem is the space between My and Files.  In general, space is a delimiter in the Unix/Ubuntu world and, unless you do something to suppress its delimiting effect, the space will terminate the item that has been parsed.

In the Unix world, people do not usually try to embed spaces into names.  It is possible to get around this but it's a nuisance.  Better to either run together the pieces of the name (e.g. MyFiles) or to use an underscore (My_Files) or a dash (My-Files).

quadproc

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
But how would I add it to this. This is, so far, the only version of the script to almost work properly

```
#All movies become G1 movies!!!
#!/bin/sh
cd /media/storage/Movies/
CMD=`find ./ -type f -name *.avi`
CMD1=`ffmpeg -i $i -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 /media/ext/Mine/$i.mp4`
echo $CMD
sleep 3

for i in `$CMD`; do $CMD1

cd

done
```

I'm so horrible at this but as much as I am horrible, I am determined to get this to work. Thanks for the help insofar.

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
> **quadproc said:**
> As other posters have implied, the problem is the space between My and Files.  In general, space is a delimiter in the Unix/Ubuntu world and, unless you do something to suppress its delimiting effect, the space will terminate the item that has been parsed.

In the Unix world, people do not usually try to embed spaces into names.  It is possible to get around this but it's a nuisance.  Better to either run together the pieces of the name (e.g. MyFiles) or to use an underscore (My_Files) or a dash (My-Files).

quadproc

So I should be making a mass rename script in stead?

---

### Post by carlosgs91 on 2010-03-30
.

---

### Post by kerry_s on 2010-03-30
> **blur xc said:**
> imho- quotes work better in scripts than backslashes.  Example-
```
file="/home/john/my file"
destination="/home/jane/stupid files/"
cp "$file" "$destination"
```although I would imagine 
```
file=/home/john/my\ file
destination=/home/jane/stupid\ files/
cp "$file" "$destination"
```would work as well...  I just like keeping it consistent.

BM

i always use "quotes" in my scripts, but both work.

---

### Post by blur xc on 2010-03-30
> **Sin@Sin-Sacrifice said:**
> But how would I add it to this. This is, so far, the only version of the script to almost work properly

```
#All movies become G1 movies!!!
#!/bin/sh
cd /media/storage/Movies/
CMD=`find ./ -type f -name *.avi`
CMD1=`ffmpeg -i $i -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 /media/ext/Mine/$i.mp4`
echo $CMD
sleep 3

for i in `$CMD`; do $CMD1

cd

done
```I'm so horrible at this but as much as I am horrible, I am determined to get this to work. Thanks for the help insofar.

Um- my stab at it- 
Lose the CMD1 variable and just put that line of code inside the for loop.

```
for i in "`$CMD`"; do
    ffmpeg -i "$i" -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 "/media/ext/Mine/$i.mp4"
done
```I'm not saying the rest of your code will work either- I don't know jack about that ffmpeg line...

One thing though- When you do your find command and get all your avi files, and $i becomes the name and path for that file, you are sticking that same $i bakc into the new output path?  Seems to me like that won't work...  but I could be wrong...

To get the filename w/o the path, use the basename command (man basename), but that still won't strip the extension.  You'll need a sed or awk (I'm not an expert with those) or maybe even use the cut command to rip the fielname w/o the path or extension to add to your output filepath & name...

BM

Edit- I'd probalby also kill the cd command at the beginning, and just add the path to the find command:
```
find /media/storage/movies/ -type f *.avi
```

---

### Post by kerry_s on 2010-03-30
> **Sin@Sin-Sacrifice said:**
> But how would I add it to this. This is, so far, the only version of the script to almost work properly

```
#All movies become G1 movies!!!
#!/bin/sh
cd **"/home/john/my file"**
CMD=`find ./ -type f -name *.avi`
CMD1=`ffmpeg -i $i -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 **"/home/john/my file/$i.mp4"**`
echo $CMD
sleep 3

for i in `$CMD`; do $CMD1


cd

done
```

I'm so horrible at this but as much as I am horrible, I am determined to get this to work. Thanks for the help insofar.

my guess would be the "cd" line & the destination.

---

### Post by kerry_s on 2010-03-30
> **blur xc said:**
> Um- my stab at it- 
Lose the CMD1 variable and just put that line of code inside the for loop.

```
for i in "`$CMD`"; do
    ffmpeg -i "$i" -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 "/media/ext/Mine/$i.mp4"
done
```I'm not saying the rest of your code will work either- I don't know jack about that ffmpeg line...

One thing though- When you do your find command and get all your avi files, and $i becomes the name and path for that file, you are sticking that same $i bakc into the new output path?  Seems to me like that won't work...  but I could be wrong...

To get the filename w/o the path, use the basename command (man basename), but that still won't strip the extension.  You'll need a sed or awk (I'm not an expert with those) or maybe even use the cut command to rip the fielname w/o the path or extension to add to your output filepath & name...

BM

Edit- I'd probalby also kill the cd command at the beginning, and just add the path to the find command:
```
find /media/storage/movies/ -type f *.avi
```

:lolflag: yeah it could use some cleaning, personally i'd throw some zenity in there get some gui action.

@ Sin@Sin-Sacrifice
is this a script just run from the term, nautilus script or launcher. if you give as much detail as you can, i'm sure some genius around here can do you up a script just for you.

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
> **blur xc said:**
> Um- my stab at it- 
Lose the CMD1 variable and just put that line of code inside the for loop.

```
for i in "`$CMD`"; do
    ffmpeg -i "$i" -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 "/media/ext/Mine/$i.mp4"
done
```I'm not saying the rest of your code will work either- I don't know jack about that ffmpeg line...

One thing though- When you do your find command and get all your avi files, and $i becomes the name and path for that file, you are sticking that same $i bakc into the new output path?  Seems to me like that won't work...  but I could be wrong...

To get the filename w/o the path, use the basename command (man basename), but that still won't strip the extension.  You'll need a sed or awk (I'm not an expert with those) or maybe even use the cut command to rip the fielname w/o the path or extension to add to your output filepath & name...

BM

Edit- I'd probalby also kill the cd command at the beginning, and just add the path to the find command:
```
find /media/storage/movies/ -type f *.avi
```

Thanks a ton man... it would have taken me a month to find all that in a tutorial. I'll try it and see. Thanks to carlosgs91... I need that too. I had one bookmarked but it's gone now. Thanks everyone else too.

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
> **kerry_s said:**
> :lolflag: yeah it could use some cleaning, personally i'd throw some zenity in there get some gui action.

@ Sin@Sin-Sacrifice
is this a script just run from the term, nautilus script or launcher. if you give as much detail as you can, i'm sure some genius around here can do you up a script just for you.

terminal

---

### Post by blur xc on 2010-03-30
Ok- I've been playing aroudn some more, and personally (I'm still a scripting newb) I've never gotten a find and for loop to work the way you have it written, though I would love for a scripting guru to come it and show how to make it work.  Every time I end up doing something like this, which works on my machine:

```
#!/bin/bash

find /media/storage/videos/ -name *.avi > testfile.txt

while read FILE; do
    NAME="`basename "$FILE" .avi`"
    cp "$FILE" "testdir/$NAME.mp4"
done < testfile.txt

exit 0
```

Just replace my cp line with your ffmpeg line.  This places the output of the find command in to a temporary text file.  Then the for loop reads each line of the text file one by one and executes your command on each file.

If you are feeling cool- add an rm testfile.txt to the end (before the exit 0).

My input files:
```
cat testfile.txt 
/media/storage/videos/stupid videos1.avi
/media/storage/videos/stupid videos3.avi
/media/storage/videos/stupid videos5.avi
/media/storage/videos/stupid videos8.avi
/media/storage/videos/stupid videos7.avi
/media/storage/videos/stupid videos9.avi
/media/storage/videos/stupid videos6.avi
/media/storage/videos/stupid videos0.avi
/media/storage/videos/stupid videos4.avi
/media/storage/videos/stupid videos2.avi
```

output files:
```
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos0.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos1.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos2.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos3.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos4.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos5.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos6.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos7.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos8.mp4
-rw-r--r-- 1 mickey mouse 0 2010-03-30 15:36 stupid videos9.mp4
```

Good luck!
BM

---

### Post by Sin@Sin-Sacrifice on 2010-03-30
Hey blur... thanks again man. That actually works well. The cp command would be perfect aside from the fact that I'm converting these for a T-Mobile G1. So I need to change bitrate, resolution, and aspect ratio too. It works when I substitute the cp command with my ffmpeg command but it tries to execute them all at the same time. I don't know. Maybe someone out there knows.

---

### Post by DaithiF on 2010-03-31
I would do it something like this:
```
find /media/storage/videos/ -name *.avi | while read FILE
do
NAME=$(basename $FILE)
ffmpeg -i "$NAME" -f mp4 -vcodec libx264 -vpre ultrafast -acodec libfaac -ab 192 -s 320x240 -aspect 4:3 -threads 4 "/media/ext/Mine/${NAME%.avi}.mp4"
done

```

---

