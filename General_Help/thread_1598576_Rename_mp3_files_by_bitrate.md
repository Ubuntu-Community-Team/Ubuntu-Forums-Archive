---
title: "Rename mp3 files by bitrate"
date: 2010-10-16
forum: General Help
---

### Post by AlphaLexman on 2010-10-16
I want to rename my *.mp3 files by the bitrate (kb/s) they were ripped.

e.g.
```
~/Music/Red_Hot_Chili_Peppers/Californication/01.Around_the_World.mp3
```to:
```
~/Music/Red_Hot_Chili_Peppers/Californication/01.Around_the_World.256.mp3

```or,
```
~/Music/Fleetwood_Mac/Greatest_Hits/01.Rhannon.mp3
```to:
```
~/Music/Fleetwood_Mac/Greatest_Hits/01.Rhannon.128.mp3
```Any Ideas?

---

### Post by gnush on 2010-10-16
You might be able to make a script to do it by using one of the programs suggested _[here]("http://superuser.com/questions/36871/linux-command-line-utility-to-determine-mp3-bitrate")_, I haven't tried it myself though.

---

### Post by AlphaLexman on 2010-10-16
I guess I know I will have to use [grep, awk, and/or sed] to get what I want, I just don't know how...

---

### Post by AlphaLexman on 2010-10-23
```
id3info 01_Around_the_World.mp3 | grep Bitrate
```
will output:
```
Bitrate: 256KBps
```
How do I reduce it to just "256"?

---

### Post by AlphaLexman on 2010-10-23
> **AlphaLexman said:**
> How do I reduce it to just "256"?
```
id3info filename.mp3 | grep Bitrate | cut -c 10-12
```
> 256
Now should I set the output to a variable, and insert the varaible into a rename command?

---

### Post by AlphaLexman on 2010-10-25
Here is the script so far...

But I need some help testing if the bitrate has been added to the filename?

> if [[ `echo $FILENAME | sed 's/^.*\(...\)\..*/\1/'` = "?What_do_I_put_here?" ]]```
#!/bin/bash

    set -e

# choose search method ...

    # use this to recursively search directories
    # will not work if filenames have spaces!
    for FILENAME in $(find . -name "*.mp3")

# or,

    # use this for directory specific,
    # or if filenames have spaces
    #find ./*.mp3 -print | while read FILENAME

# end choose search method.


    
# test if audio file already has bitrate in filename?

    if [[ `echo $FILENAME | sed 's/^.*\(...\)\..*/\1/'` = "?What_do_I_put_here?" ]]

        exit 0

    fi

    do 

        BASENAME="${FILENAME%.[^.]*}"
        EXT="${FILENAME:${#BASENAME} + 1}"

    # id3info does NOT read VBR correctly!
    # vbrfix improves bitrate accuraccy but not for every file
        BITRATE=`id3info "$FILENAME" | grep "Bitrate" | cut -c 10-12`

    # this conditional only works for id3info
        if [[ $BITRATE = ??K ]]; then

        # Bitrate is less than 100
            BITRATE=0${BITRATE:0:2}

        fi

        echo $BASENAME.$BITRATE.$EXT

        # uncomment to actually rename files
        #mv -Tv "$FILENAME" "$BASENAME.$BITRATE.$EXT"

    done


```

---

### Post by AlphaLexman on 2010-10-28
It Works! (kinda) :neutral: It still needs some VBR corrections, and I would like to add 'ogg' files to the script also. But I got over the hump of testing for the existing bitrate in the filename.

```
#!/bin/bash

    set -e

    # use this to recursively search directories
    # will not work if filenames have spaces!
    for FILENAME in $(find . -name "*.mp3"); do

        # test if audio file already has bitrate in filename?
        # use 'sed' to test the three characters before the extension
        # if they are numeric characters or not.
        while [[ `echo $FILENAME | sed 's/^.*\(...\)\..*/\1/'` != *[0-9]* ]]

            do
            
                break
                
            done
    

        if [[ `echo $FILENAME | sed 's/^.*\(...\)\..*/\1/'` != *[0-9]* ]]; then

            BASENAME="${FILENAME%.[^.]*}"
            EXT="${FILENAME:${#BASENAME} + 1}"

        # id3info does NOT read VBR correctly!
        # vbrfix improves bitrate accuraccy but not for every file
            BITRATE=`id3info "$FILENAME" | grep "Bitrate" | cut -c 10-12`

        # this conditional only works for id3info
            if [[ $BITRATE = ??K ]]; then

            # Bitrate is less than 100
                BITRATE=0${BITRATE:0:2}

            fi

            echo $BASENAME.$BITRATE.$EXT 

            # uncomment to actually rename files
            #mv -Tv "$FILENAME" "$BASENAME.$BITRATE.$EXT"
    
        fi

    done
        

```enjoy!

---

