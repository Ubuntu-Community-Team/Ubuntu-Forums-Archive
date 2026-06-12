---
title: "Itunes  and audio codecs"
date: 2006-03-19
forum: General Help
---

### Post by corvax on 2006-03-19
Hello Ive been dowloading songs from the itms using sharpmusique dvd jon was nice enought to put a debian package up on his site. It works excellent but it saves the files as .m4a. I found two scripts to convert m4a to mp3 ill post them both the first one ive been using it works great but doesnt save the tag info ie.. title artist year etc which i want. The second one does but it doesnt seem to work, bear in mind im using it as is so if you  notice any errors in it let me know maybe im supposed to uncomment somthing or customize part of it but im not sure... so here they are 

the fist one that works is m4a2mp3 here........

#!/bin/sh
#
# m4a to mp3

for i in *.m4a; do

    faad "$i"
    x=`echo "$i"|sed -e 's/.m4a/.wav/'`
    y=`echo "$i"|sed -e 's/.m4a/.mp3/'`
    lame -h -b 192 "$x" "$y"
    rm "$x"

done


The second one i cant get working is m4a2mp3 -- For preserving the music info (tags) here......................

#!/bin/sh
#
# m4a to mp3

trap 'rm -f "$info" "$opts" "$wav" "$mp3"; exit 10' 1 2 3 15

for m4a in "$@"; do

 opts=` echo "$m4a"|sed -n 's/\.m4a$/.opts/p'`
 wav=`  echo "$m4a"|sed -n 's/\.m4a$/.wav/p'`
 mp3=`  echo "$m4a"|sed -n 's/\.m4a$/.mp3/p'`
 [ -z "$mp3" ] && continue

 # study it
 faad -i "$m4a" | sed -n '
   s/["`$]/\\\&/g   # handle any escapes in titles
   s/^title: \(.*\)$/--tt "\1"/p
   s/^artist: \(.*\)$/--ta "\1"/p
   s/^album: \(.*\)$/--tl "\1"/p
   s/^track: \(.*\)$/--tn "\1"/p
   s/^date: \([12][0-9][0-9][0-9]\)$/--ty "\1"/p  # year?
  #s/^genre: \(.*\)$/--tg "\1"/p   # m4a genres dont match those of mp3
  ' - > "$opts"

 # convert it
 faad "$m4a"
 #cat "$opts"   # debugging
 # Other option for lame  -b 192
 eval "lame -h "`cat "$opts"`" \"$wav\" \"$mp3\""

 # cleanup
 rm -f "$opts" "$wav"

done

---

