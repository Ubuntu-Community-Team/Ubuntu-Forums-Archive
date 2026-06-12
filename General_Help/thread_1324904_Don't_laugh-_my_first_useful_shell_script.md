---
title: "Don't laugh- my first useful shell script"
date: 2009-11-12
forum: General Help
---

### Post by blur xc on 2009-11-12
I take a lot of photos, and they are all stored in my external drive (for now) under /media/FreeAgent_Drive/Photos/YEAR/Y-M-D directory format.  When I copy files from my compact flash card over, I always have to make the directory first, then drag and drop or copy via. command line, but it's tedious.  I thought the purpose of computers (at least one purpose) is to eliminate humans from having to do repetitive tasks, right?

So- screwing around a bit, I wrote this:
```
#!/bin/bash
# Script to make folder for photos
FOLDER=`date +%Y-%m-%d`
YFOLDER=`date +%Y`

# Check if folder already exists and make one if it doesn't
if [ -d ./$YFOLDER ]
then 
    echo "Folder ./$YFOLDER already exists"
    if [ -d ./$YFOLDER/$FOLDER ]
    then
        echo "Folder ./$YFOLDER/$FOLDER already exists"
    else
        mkdir ./$YFOLDER/$FOLDER
    fi
else
    mkdir $YFOLDER
    mkdir $YFOLDER/$FOLDER
fi
exit 0
```

When I'm done I'll replace the ./ with the absolute path to where I want the photos.

I'm more than certain there's a better way to do it, but this works, and I did it all on my own w/o any help!  In the end, I intend to keep adding to it, and make it more sophisticated.  After creating the folder, I'd like it to copy the files from the CF card to the directory, then do a comparison to make sure the copy was successful, and then prompt the user and ask if he/she wants the originals off the CF card erased. 

When I'm done I'll replace the ./ with the absolute path to where I want the photos.  I'll probably also have to do a test somewhere along the way to make sure my external drive is mounted at the proper location...  Every once in a while, it'll hang and need "rebooting" (un-plug power cord, wait 30, plug back in, remount)...

Oh- and I did the whole thing in Vim...  I've got a small laminated Vim cheat sheat by my side...  

This is fun stuff...  

BM

---

### Post by undecim on 2009-11-13
congrats on your first shell script! And also with Vim--it can be a handful the first few times, but IMHO, once you learn to use it, its mighty powerful.

A little hint that would make the script a little simpler: if a parent directory doesn't exist, the child won't either. Also, the mkdir -p option will make all parent directories that don't exist in a path, so you could simplify the script to:
```
#!/bin/bash
# Script to make folder for photos
FOLDER=`date +%Y/+%Y-%m-%d`

# Check if folder already exists and make one if it doesn't
if [ -d ./$FOLDER ]
then
    echo "Folder ./$FOLDER already exists"
else
    mkdir -p ./$FOLDER
fi
exit 0
```It won't make much of a performance difference, but it makes it easier to read, and that's important.

You may want to test that yourself though, because I didn't

Again, nice job for a first script. Isn't bash great?

---

### Post by fargle on 2009-11-13
Nothing to laugh about that I can see, I've been doing shell scripting since 1992 and that's pretty much the exact code I would have written, so you're doing well.

Glad you're having fun!  If you want a real laugh sometime, try to do that with a DOS .BAT file and marvel at the absolute travesty you'll have created.

Keep it up!  And of course, vi is the One True Editor, so congratulations on sticking with it and not bailing out to pico or something equally ridiculous.  Every Unix system you'll ever see will have vi on it, that's not the case for other editors, including Emacs (ugh).

---

### Post by blur xc on 2009-11-13
> **undecim said:**
> congrats on your first shell script! And also with Vim--it can be a handful the first few times, but IMHO, once you learn to use it, its mighty powerful.

A little hint that would make the script a little simpler: if a parent directory doesn't exist, the child won't either. Also, the mkdir -p option will make all parent directories that don't exist in a path, so you could simplify the script to:
```
#!/bin/bash
# Script to make folder for photos
FOLDER=`date +%Y/+%Y-%m-%d`

# Check if folder already exists and make one if it doesn't
if [ -d ./$FOLDER ]
then
    echo "Folder ./$FOLDER already exists"
else
    mkdir -p ./$FOLDER
fi
exit 0
```It won't make much of a performance difference, but it makes it easier to read, and that's important.

You may want to test that yourself though, because I didn't

Again, nice job for a first script. Isn't bash great?

Wow- that makes it a bit shorter!  I'll test it out, and see how it goes...  Doing the nested logic was fun though.  I haven't written any kind of code in over 5 years, and that was visual basic functions, mostly for MS Excel.  Before that, it was in high school doing Q-basic, Amiga Basic, and Apple IIe/Commodore 64 basic (pretty much the same as I recall)...  I only ever did a little in MS-DOS .BAT files, and definitely nothing very complicated.  

thanks or the encouragement!

BM

Edit- the condensed code worked like a charm...

---

### Post by JairunCaloth on 2009-11-13
It's a great feeling when you write your first useful bash script :)

Slightly off topic of scripting. For getting more comfortable in Vim, I highly recommend vimtutor. There is a good chance it's already installed on your system. If not, you can grab it from the repos.

Also I don't know if you already have it turned on, but Vim syntax highlighting is very helpful to me when I'm coding. To turn it on from inside vim, in command mode

:syntax on

To turn it off, its just simply

:syntax off

There are a few color schemes that come with a default Vim installation, and you can change them on the fly with 

:colorscheme <name>

Tab completion works here, so you can tab through to see the various color schemes. Once you've found a color scheme you like and want to make it permanent open up your ~/.vimrc and add the lines to the file

syntax on
set colorscheme <name>

---

### Post by Bonster on 2009-11-15
Something related to this, that I would like to ask is.

How would I make it to select "no" when it prompts to overwrite a existing file? So I dont have to press "N" everytime =)

Thanks


Heres what i got so far for my conversion:

********
for movie in *.avi ; do
    echo Processing "$movie"

ffmpeg -i "$movie" -f mp4 -b 1800 -maxrate 2500 \
       -vcodec libxvid -qmin 3 -qmax 5 -s 320x240 \
       -acodec libfaac -ab 128 \
       ~/Downloads/youtube/"$movie.mp4"
*************


---------
File '/home/bonster/Downloads/youtube/anaconda4.avi.mp4' already exists. Overwrite ? [y/N] 
------

What I want it to do:
Select No for all existing file and skip to the next file

---

### Post by JairunCaloth on 2009-11-23
Looks like ffmpeg has a cli option to always overwrite, but I don't see an equivalent option to never overwrite.

Maybe look into expect. I've never used it, but it seems like it might be useful here.

---

