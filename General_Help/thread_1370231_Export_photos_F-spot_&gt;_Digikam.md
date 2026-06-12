---
title: "Export photos F-spot &gt; Digikam"
date: 2010-01-02
forum: General Help
---

### Post by Levviathor on 2010-01-02
I have upward of 1400 photos in F-spot, organized by hierarchal tags, example: "People/joe, People/jim, Events/camping" etc.

However, I want to use Digikam now.  Fickle me.

Is there any way to export from F-spot to Digikam and keep the tags (mostly) intact?

---

### Post by Levviathor on 2010-01-04
Bump.

---

### Post by Levviathor on 2010-01-06
Anybody

---

### Post by hugoheden on 2010-01-11
> **Levviathor said:**
> I have upward of 1400 photos in F-spot, organized by hierarchal tags, example: "People/joe, People/jim, Events/camping" etc.

However, I want to use Digikam now.  Fickle me.

Is there any way to export from F-spot to Digikam and keep the tags (mostly) intact?

I've been hitting refresh on this one for a week now -- I am also interested in this.. Though I've also experimented with Digikam a bit and (when run within a Gnome environment etc) it's not that much of an improvement over F-spot. 


(The new gthumb[1] 2.11.1 seems a lot more promising[2]. But then, how would one export/import all those tags from F-spot to gthumb? Does gthumb handle tags at all? That's for another thread I guess.)

[1] [http://live.gnome.org/gthumb](http://live.gnome.org/gthumb)
[2] [http://mail.gnome.org/archives/gthumb-list/2010-January/msg00012.html](http://mail.gnome.org/archives/gthumb-list/2010-January/msg00012.html) -- you'll have to compile it from source.

---

### Post by strangedata on 2010-12-31
Let's revive this thread, shall we?

After the major screw-up in f-spot on ubuntu 10.10 not being able to correctly manage dates for raw files, I decided to move to digiKam, but I couldn't find a way to migrate my tags.

Has anyone found a solution for this?

cheers!

---

### Post by patmagee1024 on 2011-05-19
This should give you a head start. It populates the xmp section in each file with the f-spot AND digikam tags based on a query from the f-spot database. It only does the tags tho. 

Prerequisites:
The source of information is supplied by the f-spot sqlite database. The default location is ~/.config/f-spot/photos.db. If yours is in a different location, modify the location in the script.

The script PRESUMES your files have no xmp tags. It does no error checking, it simply pokes the information in place into each file. If the info is already there you will have duplicate information. To remove all xmp info for each file I used ```
exiv2 rm -dx *.jpg
``` from another script. For a large directory structure full of files, consider this:
```
#!/bin/bash

# Strips all exif information out of images
# Run this from the top of the directory structure with photos
clear
echo "This is strip-exif.sh"
d=$( pwd )
file1=./strip-exiv.tmp

find -name '*.jpg' -print > $file1
find -name '*.JPG' -print >> $file1

cat $file1 | xargs -I{} exiv2 rm -dx "{}"
rm $file1
exit
```Backup your photos.db. This script doesn't make any changes to the db, but better safe than sorry.

The actual script:

```
#!/bin/bash

# This script was written and used in Ubuntu 10.04 LTS.
# 
clear
echo "This is exiv-push.sh"

# Set up file info
d="/home/user/Photos"
qry=$d/qry-exiv2-info.txt

# This pulls the data out of the database directly
sqlite3 ~/.config/f-spot/photos.db "SELECT photos.filename, tags.name FROM (photos INNER JOIN photo_tags on photos.id = photo_tags.photo_id) INNER JOIN tags on photo_tags.tag_id = tags.id;" | sed 's/|/,/g' > $qry

while read line
do
    name1=$(echo $line | awk -F "," ' {print $1}')        # Get file name
    name=$(echo $name1 | sed -e 's/%20/ /g')       # Deal with spaces being named differently in the db
    tag=$(echo $line | awk -F "," ' {print $2}')        # Get tag
    striptag=$(echo $tag | tr -d \\r)                      # Strip the trailing <cr>
    find -name "$name" -exec exiv2 -M"set Xmp.dc.subject XmpBag '$striptag'" {} \; | sh
    find -name "$name" -exec exiv2 -M"set Xmp.digiKam.TagsList '$striptag'" {} \; | sh
done < $qry
exit
```The script will take a while to run if you have lots of images, slow drive, etc. I hope you find it useful. It should get you over the hump of getting the tags in place on all your files even if f-spot didn't get them into the files (as was my problem initially.) I added the digiKam tags so I could evaluate the tag features side by side with f-spot.

Regards.

---

### Post by Menschenfresser on 2011-09-02
I hope this is not too late for Levviathor (and others). I also wanted to use Digikam for my photos, as f-spot was crashing regularly on me and was simply not as powerful as digikam (what is!), so I wrote a python script that manages the migration:

[https://bitbucket.org/rolandgeider/f-spot-to-digikam](https://bitbucket.org/rolandgeider/f-spot-to-digikam)

It can copy the tags, ratings and comments.

---

