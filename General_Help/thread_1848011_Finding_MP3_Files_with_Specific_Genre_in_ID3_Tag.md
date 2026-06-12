---
title: "Finding MP3 Files with Specific Genre in ID3 Tag"
date: 2011-09-21
forum: General Help
---

### Post by Kissell on 2011-09-21
I have a large MP3 collection that I need to thin down to fit on a portable device.  I thought a good way to do this would be to separate my files by genre, as I like to listen to different types of music at home versus on the go.

My MP3 files do have accurate ID3 tags...  Can someone tell me a magical command-line search for those files in linux?  Something that would let me move all files of a specific genre to a new folder?

---

### Post by Porcini M. on 2011-09-22
It would be something along the lines of:

for f in `ls` ; do if [ "`mp3info -p %g $f`" == "Hip-Hop" ]; then mv $f /mynewdir ; fi ; done

EDIT: this has trouble with filenames with spaces in it though... Not sure how to fix that, enclosing $f with quotes doesn't work...

---

### Post by Kissell on 2011-09-22
Groovy!  

After installing mp3info ```
sudo apt-get install mp3info
``` this works really well.  

It's moments like this that remind me of why I love linux.  The command line is so powerful, and there's almost always a way to do what you want quickly, easily, for free, and scriptable.  

Only problem is this doesn't work if there is a " " (space character) in the filename.  I tried putting quotes around the variable, but nothing I've tried worked from the command line yet.  With the knowledge that mp3info exists I can write a bash script now... but would appreciate a command line solution if you have one, I'm evidently lacking in some knowledge that solution could teach me.

---

### Post by patryk77 on 2011-09-22
> **Porcini M. said:**
> It would be something along the lines of:

for f in `ls` ; do if [ "`mp3info -p %g $f`" == "Hip-Hop" ]; then mv $f /mynewdir ; fi ; done

**EDIT: this has trouble with filenames with spaces in it though... Not sure how to fix that, enclosing $f with quotes doesn't work...**

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
Pitfalls 1 and 2 says how to get around the spaces.

But that doesn't actually work recursively and using *.mp3 won't fix that...

---

### Post by Kissell on 2011-09-22
> **patryk77 said:**
> 
that doesn't actually work recursively and using *.mp3 won't fix that...

We could try switching away from "ls" and use "find . .mp3" which should work for everything recursively.

---

### Post by patryk77 on 2011-09-22
> **Kissell said:**
> We could try switching away from "ls" and use "find . .mp3" which should work for everything recursively.

Nope, find won't let you use spaces either :P

Your best bet would be to use a scripting language like Perl, I think.

---

### Post by Porcini M. on 2011-09-22
Here we go:

find -print0 | while read -d $'\0' f ; do mp3info -p %g "$f" ; done


Boo-ya! 8)

Now just need to work that into the file moving logic.

---

### Post by Kissell on 2011-09-22
Took a little hammering and going back to reference previous scripts I'd written with the help of other kind folk in these forums...  ended up with a solution that works for me.  It is really important to create that variable "X"...  when I try to run the command directly in the "if" statement it has the same'ol'problem.  But if I store the result in a variable and then use that variable in the conditional statement, it works fine.

```

#!/bin/bash

PATH_TO_MP3="/media/Data/Music/Source"
DESTINATION="/media/Data/Music/Destination"
GENRE="Country"

sudo find .mp3 "$PATH_TO_MP3" > /tmp/mp3genre.txt
FILES=/tmp/mp3genre.txt

COUNTER=0
TOTAL_LINES=`wc -l $FILES`
TOTAL_LINES=`expr "$TOTAL_LINES" : '\([0-9]*\)'`
while [ "$COUNTER" -lt "$TOTAL_LINES" ]
do
  let COUNTER=COUNTER+1
  FILE_LINE=`head -n $COUNTER $FILES | tail -n 1`

  X=`mp3info -p %g "$FILE_LINE"`
  if [ "$X" == "$GENRE" ]; then
    mv "$FILE_LINE" $DESTINATION
  fi
done

sudo rm /tmp/mp3genre.txt
exit 0

```

This will move all .mp3 files from the source folder and all subfolders to the destination folder if the mp3 genre is "Country" (set via declared variable).  

This works great for me, because all my ID3 tags are correct and all my filenames are named "artist - album - track - title.mp3" so it is okay that they are all dumped/mixed into a single directory.  

NOTE: This just moves the files, it doesn't clean up directory structure, so after this I just go back to the source and sort by the number of files in the folders and delete any empty folders from the GUI.  This might be a problem if you had files in album subfolders.

I would love to store music in folder by Genre then Artist, but that can be hard to define.  Now, if I could just find a way to identify an artist's genre...  I made my tag's genres as best I could, but the line between "Punk & Alternative & Indie" is pretty blurry sometimes, at least to me...  I can't see it clearly like I can the difference between Gangsta Rap and Classical Piano music.

---

### Post by Kissell on 2011-09-22
> **Porcini M. said:**
> Here we go:

Boo-ya! 8)


Just for the heck of it...  I finished up the command line solution, because I love that you can do it all in one line...  but in all practical usage, I'll probably just store the script and run it when I need to, without having to remember all this to type on the command line.

> 
find -print0 | while read -d $'\0' f ; do X=`mp3info -p %g "$f"` ; if [ "$X" == "Country" ]; then mv "$f" /media/Data/Music/Destination ; fi ; done


:popcorn:

---

