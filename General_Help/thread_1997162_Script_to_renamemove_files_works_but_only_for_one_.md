---
title: "Script to rename/move files works but only for one file"
date: 2012-06-04
forum: General Help
---

### Post by OliverHaslam on 2012-06-04
Hi,

I wasn't sure whether to put this into the Programming sub-forum, but it didn't really seem to fit.

I'm playing with scripts - learning hopefully - and I want to rename and then move some files based on their original name, if that makes sense. You'll see what I mean when you see what I've written.

The problem is, the script works fine if there is only one file in the source directory, but add another and it returns errors. I assume it's something glaringly obvious, but I'm a n00b so I'm stuck.

Here's what I've got:

```
#!/bin/bash

DATE=`ls ~/Dropbox/Apps/Cambox/*.jpg | sed s/.*b//g | sed s/-.*//g`
DAY=`ls ~/Dropbox/Apps/Cambox/*.jpg | sed s/.*b//g | sed s/-.*//g | sed -e 's/^.*\(..\)$/\1/'`
TIME=`ls ~/Dropbox/Apps/Cambox/*.jpg | sed -e 's/^.*\(............\)$/\1/' | sed s/-.*//g`
MONTH=`date | awk '{print $2}'`

mv ~/Dropbox/Apps/Cambox/*.jpg ~/Dropbox/Apps/Cambox/$TIME.jpg

mv ~/Dropbox/Apps/Cambox/*.* ~/Pictures/2012/$MONTH/$DAY

```

There are probably better ways to do the variables, but there you go.

Any ideas as to what I'm missing? Like I say, it works perfectly with just one file present.

Cheers.

---

### Post by steeldriver on 2012-06-04
well for one thing I would think you need to actually loop over the files - if you use wildcards in the DATE, TIME etc. assignments, then as soon as there are multiple files your ls | sed commands are going to concatenate ALL the values to a single $TIME and $DAY variable, then you will try to mv EVERY file to that one location (which will likely be malformed in any case because the file list will include spaces)

just execute them one by one at the command line and you will see what I mean

also mv will not create the target path so it will fail if the path does not exist

and your sed syntax could be tidied up - I don't know what patterns you are trying to match but you might want to look at the \{n\} syntax to match exactly n instances

also I guess your 1st move is an attempt to rename the file in-place and then the second one should move it? but the second mv is just going to mv *.* (including any remaining *.jpg) files

---

### Post by OliverHaslam on 2012-06-04
> **steeldriver said:**
> well for one thing I would think you need to actually loop over the files - if you use wildcards in the DATE, TIME etc. assignments, then as soon as there are multiple files your ls | sed commands are going to concatenate ALL the values to a single $TIME and $DAY variable, then you will try to mv EVERY file to that one location (which will likely be malformed in any case because the file list will include spaces)

just execute them one by one at the command line and you will see what I mean

also mv will not create the target path so it will fail if the path does not exist

and your sed syntax could be tidied up - I don't know what patterns you are trying to match but you might want to look at the \{n\} syntax to match exactly n instances

I'll do some digging on loops then. Not something I've used, so thanks for that.

The script works perfectly if there is only one file involved, so all the paths and variables obviously work. The targets exist, etc. It's just something to do with the way the mv works with multiple files.

Oh, and I have no doubt the variables could be better. I'm learning as I go along :D

Cheers.

---

### Post by steeldriver on 2012-06-04
something like

```
for FILE in $(ls *.jpg)
do
      DATE=$(echo $FILE | sed 's/.*b//g' | sed 's/-.*//g')
      .
      .
      mv .  .  .
done

```

---

### Post by OliverHaslam on 2012-06-05
Thanks.

I've tried that, and now it moves correctly but is not renaming the files.

The errors I get are:

```
mv: target `/home/olivm/Dropbox/Apps/Cambox/011325.jpg' is not a directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.jpg': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.*': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.jpg': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.*': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.jpg': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.*': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.jpg': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.*': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.jpg': No such file or directory
mv: cannot stat `/home/olivm/Dropbox/Apps/Cambox/*.*': No such file or directory
```

The script now looks like:

```
#!/bin/bash

for FILE in $(ls ~/Dropbox/Apps/Cambox/*.jpg)
do
        DATE=$(echo $FILE | sed 's/.*b//g' | sed 's/-.*//g')
        DAY=$(echo $FILE | sed s/.*b//g | sed s/-.*//g | sed -e 's/^.*\(..\)$/\1/')
        TIME=$(echo $FILE | sed -e 's/^.*\(............\)$/\1/' | sed s/-.*//g)
        MONTH=`date | awk '{print $2}'`

        mv ~/Dropbox/Apps/Cambox/*.jpg ~/Dropbox/Apps/Cambox/$TIME.jpg
        mv ~/Dropbox/Apps/Cambox/*.* ~/Pictures/2012/$MONTH/$DAY
done


```


Cheers.

---

### Post by steeldriver on 2012-06-06
The idea of looping is that you **operate on one file at a time** from the ls (i.e. $FILE)

```
 mv ~/Dropbox/Apps/Cambox/$FILE ~/Pictures/2012/$MONTH/$DAY/$TIME
```

You still have wildcards in the mv commands e.g.

```
mv ~/Dropbox/Apps/Cambox/*.* ~/Pictures/2012/$MONTH/$DAY
```

which is going to empty the source directory of every single suffixed   file (*.*) the first time through the loop, so of course it can't stat   (locate) the remaining .jpg files on subsequent iterations (they're already in ~/Pictures/2012/$MONTH/$DAY)

---

### Post by CaptainMark on 2012-06-07
I have a similar script, you are more than welcome to make use of it, im sure if you want to learn bash, it would be good practice to tweak it to remane your files as you go, you need to install a package called jhead for it to work straight (its in the standard repos) ```
#!/bin/bash

# Photo Sorter
# A script to sort photos in date ordered directories
# Mark Skinner
# Created 04/03/2012
# Requires jhead to be installed

count=0

for photo in $(ls $HOME/Pictures/ | grep -i -e jpg -e jpeg); do
    timestamp=$(jhead $HOME/Pictures/$photo | grep Date/Time)
    year=${timestamp:15:4}
    month=${timestamp:20:2}
    if [ $year ] && [ $month ]; then
        mkdir -p $HOME/Pictures/$year/$month; mv -n $HOME/Pictures/$photo $HOME/Pictures/$year/$month/ && let count=$count+1
        fi
    done

if [ $count != 0 ]; then
    notify-send -t 30000 "Photo Organiser" "$count Photos archived in Pictures folder"
    fi

```

---

### Post by OliverHaslam on 2013-01-13
Thanks for that, I'll take a look.
 
Sorry for the crazy-late reply, too! ;)

---

### Post by Vaphell on 2013-01-13
use of **ls** to generate the lists of files is a big no-no.
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

```
for FILE in [COLOR="Red"]$(ls ~/Dropbox/Apps/Cambox/*.jpg)[/COLOR] # wrong
for FILE in [COLOR="Blue"]~/Dropbox/Apps/Cambox/*.jpg[/COLOR] # ok
```

I'd suggest some code but without knowing the inputs and expected outputs it's hard to create a tidy solution.

---

