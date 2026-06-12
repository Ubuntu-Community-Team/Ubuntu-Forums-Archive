---
title: "Help with a script (cp, mv, directory variables)"
date: 2009-11-06
forum: General Help
---

### Post by kumoshk on 2009-11-06
I'd like some help writing a script.

I want the script to do the following:
* start in a certain directory
* make a directory; we'll call it deposit
* enter every other directory (besides deposit) in the folder, one at a time, and do the following in each:
** Well, first you should know every other directory besides deposit has a folder called wav in it
** Rename the wav directory to the name of the folder it is in.
** Move that folder to the deposit directory

I know how to do all of that, except two things:
* Determining the name of the folder you're in so that you can use it for the new name of something in the folder
* Entering all the other folders, except deposit, one by one (perhaps recursively); they're all named with numbers, but there is an arbitrary number of them, by the way.

The reason for this script is to preserve and separate the wav files from the ogg files I've encoded from them. I mean, I still want the wav files, but I don't want them mixed in with my ogg files (I don't want to copy huge wav files everywhere I copy the ogg files, and removing them manually without deleting them is inconvenient), but the wav files from each CD need to be in different folders, with names making the disc number.

I'll be using this script a lot, if we can get it working.

Here's some pseudo-code of what I want:
```

mkdir deposit
for every intDirName in curDir do
    cd intDirName
    mv -r wav ../deposit/intDirName

```

Does that make sense?

---

### Post by lloyd_b on 2009-11-06
To answer one question, you can get the name of the current directory via the 'pwd' command:```
CURDIR=`pwd`[\CODE](the backtics (`) tell the system to execute the 'pwd' command, and store the output in the shell variable CURDIR.

But you don't really need to 'cd' into any of the directories, if I'm understanding the requirements.  Just a series of "mv" commands will do the trick, with the full path specified.

Here's a rough shot at the script:[CODE]#!/bin/bash
# Change the line below for the actual directory...
STARTDIR="/home/user/somewhere"

# Make the "deposit" subdirectory
mkdir $STARTDIR/deposit

# Loop through the subdirectories under STARTDIR
for CURDIR in $STARTDIR/*; do
    # See if there's a "wav" subdirectory
    if [ -d $CURDIR/wav ]; then
        # Extract the "basename" (just the directory name) from CURDIR.  I'm
        # using bash's string handling because it's faster than the 'basename' command
        BASENAME=${CURDIR##*/}
        # Move the "wav" subdirectory to "deposit/$BASENAME"
        mv $CURDIR/wav $STARTDIR/deposit/$BASENAME
    fi
done
```

If I understood your requirements correctly, that should do the trick.  Note that I can't guarantee this won't mess up any files, so be sure to test it after making backups of the files in question...

Lloyd B.

---

### Post by kumoshk on 2009-11-06
Thanks!

It works great. The only trouble I had was getting the starting directory in a variable. I'm not sure how to assign the result of pwd to a variable.

Anyway, I managed it by making it equal to "1/../", since "1" is always going to be a known directory in this process. I could have done it with deposit, I guess.

Anyway, is there a cleaner way for that?

Can you explain how the ##*/ syntax works?

Anyway, the script does work, so these questions are just extras. Thanks for the help!

---

### Post by lloyd_b on 2009-11-07
> **kumoshk said:**
> Thanks!

It works great. The only trouble I had was getting the starting directory in a variable. I'm not sure how to assign the result of pwd to a variable.

Anyway, I managed it by making it equal to "1/../", since "1" is always going to be a known directory in this process. I could have done it with deposit, I guess.

Anyway, is there a cleaner way for that?

Can you explain how the ##*/ syntax works?

Anyway, the script does work, so these questions are just extras. Thanks for the help!

Assigning the output of a command to a variable is simple (I included this in my previous post, but something went weird with my CODE tags, so it wasn't that easy to see):```
STARTDIR=`pwd`
```Surrounding the 'pwd' command with backtics (it's the key above <Tab> on US keyboards) tells the shell to return the output from running the command.  In this case, it runs 'pwd', and takes the result and puts in into STARTDIR.

The "${VAR##*/}" is a string manipulation using a pattern.  The "*/" says "Any string ending in a slash character".  The "VAR##" tells it "return VAR after removing from the front the longest string matching the pattern".

I'm not very good at explaining this - perhaps you should Google "bash string manipulation" to see if there's a better explanation on the web (you can look at the man page for bash, but it's only a good explanation if you already understand the basics).

Lloyd B.

---

### Post by kumoshk on 2009-11-07
> **lloyd_b said:**
> Assigning the output of a command to a variable is simple …
Ah, I always wondered why people used those—backtics, you called them? Good to know they have a better name than backwards quotes.

Thanks for all the information. It should help a lot.

---

