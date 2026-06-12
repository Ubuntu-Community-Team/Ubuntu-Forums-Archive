---
title: "Help using the rename command with ascending numbers"
date: 2011-03-14
forum: General Help
---

### Post by evilsoup on 2011-03-14
In a moment of madness I decided to reorganise my mp3 player. I am putting everything into one folder (called 'all'), but first I am renaming the files to the following format:

artist ## songtitle

where ## is a number like 01, 02. This has been pretty straightforward with the songs that already started with a number, because then I could just

rename 's/(\d\d)/artist $1/' *.mp3

but I have a problem with those tracks that don't already have the track-numbers at the beginning. I suppose what I am asking is: can I turn

All Along the Watchtower.mp3
Purple Haze.mp3
Hey Joe.mp3

into

01 All Along the Watchtower.mp3
02 Purple Haze.mp3
03 Hey Joe.mp3

?

Any help would be much appreciated.

---

### Post by evilsoup on 2011-03-15
Nevermind, I spent the night crafting a short bash script. If anyone would find this useful, feel free to help yourself, but BE CAREFUL; this will add 01-infinity to the front of everything it sees. If you want to label a specific album or works of an artist separately, put them into a separate folder and then use this script.

```

#!/bin/bash

nameword=1
count=`ls -l | grep ^-r | wc -l`

until [ $nameword -gt $count ]; do

if [ $nameword -lt 10 ]; then
ls | head -$nameword | tail -1 | rename 's/\d*\s*(\D*.*)/0'$nameword' $1/'
nameword=$((nameword + 1))

else
ls | head -$nameword | tail -1 | rename 's/\d*\s*(\D*.*)/'$nameword' $1/'
nameword=$((nameword + 1))
fi

done

exit 0

```

---

