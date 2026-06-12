---
title: "mencoder script to convert whole folder"
date: 2010-07-07
forum: General Help
---

### Post by shortridge11 on 2010-07-07
I'm looking for help to write a little script to convert a whole folder of .mkv to .avi. This is the mencoder bit i've been using to do so
```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o [file destination] [source file] 1/"
```
and it seems to work fine.  what i'm looking for is the ability to go into a directory and use the script like so
```
convertScript /media/move/here/
```
and have all of the converted files stored in /media/move/here. It would be good if they had the same names too.  Any ideas on how i should do this?

---

### Post by DaithiF on 2010-07-07
Hi, something like this:
```
destdir=$1
[[ -z "$destdir" ]] && { echo "No destination parameter supplied, exiting"; exit 1; }
[[ ! -e "$destdir" ]] && { echo "Destination dir $destdir does not exist, exiting"; exit 1; }
destdir=${destdir%/}      # strip off any trailling / as we will add one ourselves 
for file in *.mkv
do
  newfilename="${file%.mkv}.avi"
  echo mencoder blah blah -o "$destdir/$newfilename" "$file"
done

```

remove the echo prefix to the mencoder line when you're happy to run it for real

---

### Post by shortridge11 on 2010-07-07
that worked beautifully, and you are awesome. thanks a lot =D

---

