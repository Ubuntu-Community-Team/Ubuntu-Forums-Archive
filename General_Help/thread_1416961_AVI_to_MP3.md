---
title: "AVI to MP3"
date: 2010-02-26
forum: General Help
---

### Post by mmrtnt on 2010-02-26
[SIZE="4"]Found [this thread]("http://ubuntuforums.org/showthread.php?t=183887"), which is closed.

I wrote a tiny script to do this, hope this is the place to share it.[/SIZE]

[FONT="Courier New"]```
#!/bin/bash
#
# avi2mp3.sh
# Usage: avi2mp3.sh somefile.avi audiofile.mp3

if [ $# -lt 2 ] 
then
        echo ""
        echo "Not enough args, INPUT_AVI_FILENAME OUTPUT_MP3_FILENAME";
        echo ""
        exit;
fi

# Not used here, but good to know
EXT=`echo $1 | sed -e 's/^.*\.//'`
NAME=`basename $1 ".$EXT"`

mplayer -vo null -ao pcm:file=tmp.wav $1

lame -h tmp.wav $2

rm -r tmp.wav
```[/FONT]

---

### Post by ubunterooster on 2010-02-26
Very helpful. [not trying to be annoying, but if posting a how-to, the thread name should say "how-to"]

---

### Post by mmrtnt on 2010-02-26
> **ubunterooster said:**
> ...if posting a how-to, the thread name should say "how-to"

Thanks!  I was prompted to select a category, and "SOLVED" was the only thing that seemed to match.  

I'll pay closer attention next time.

---

