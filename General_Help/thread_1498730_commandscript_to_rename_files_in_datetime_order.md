---
title: "command/script to rename files in datetime order?"
date: 2010-06-01
forum: General Help
---

### Post by dchurch24 on 2010-06-01
Hi,

I'm trying to rename all files in a folder as such:

1.jpg
2.jpg
3.jpg

Renaming them is no problem, the problem I have is, they need to be in order of the datetime that they were taken, so that the 1.jpg would be the oldest file there. The difference in filetimes is going to be very small, around 3 or 4 tenths of a second.

The reason I need to do this is that I have another script (not quite finished yet), that takes the next three files in a loop and applies qtpfsgui to them to output an HDR image to another folder, then move on to 4,5 & 6, and: repeat.

Any idea how to do this, I'm sure it's probably very easy and I'm simply not finding it?

---

### Post by StuartN on 2010-06-01
> **dchurch24 said:**
> they need to be in order of the datetime that they were taken

If you don't care what the name is, only the order, then this will rename files in time order when their times are AT LEAST one second apart:

```
for file in * ; do mv $file $(stat -c %Y $file) ; done
```

Changing %Y to %y should give you horrible filenames with fractional seconds.

---

### Post by dchurch24 on 2010-06-01
Hi, 

thanks for that.

I DO care what the names are.

In my other script, I intend to pick up every third image by name, so 3.jpg (then 4 & 5), then 6.jpg (then 7 & 8 ) etc...

```

Pseudo:

for X = 1 to ImageCount step 3                                   ' (wow - that takes me back!)
   qtpfsgui -a MTB -s outputnameX.hdr -o testhdrX.jpg (imageX).JPG (imageX+1).JPG (imageX+2).JPG
next

```

So as 1 should be before 2 and 3, they need to be named in order.

---

### Post by BoneKracker on 2010-06-01
You can't really rely on file modification times.  If you really want the date the picture was taken, you should use its exif data.

If you have imagemagick installed (which you probably already do), you can list the exif data with```

identify -verbose $filename
```

From that, you can use sed or awk to parse the date/time group when the picture was taken.

So I would probably create an associative array and make a loop to populate it with each file's name and the date/time it was originally taken.  Pseudocode somethign like:

```
Create array
i=0

for file in *.jpg; do
    identify -verbose $file > tmp
    dtg=$(sed or awk to parse the date/time)
    assign jpeg filename to array[i,0]
    assign dtg to array[i++,1]
done

```
Then you need to sort and rename.

You could actually sort during the population of the array, but doing it separately would be conducive to fault isolation as you're debugging, be more modular, might be more efficient, and should allow you to more easily incorporate some existing sort algorithm.

Renaming, of course, can't happen until the entire sort has been completed.  As you said, you've got that part figured out.

---

### Post by dchurch24 on 2010-06-01
Thank you.

I thought I'd need to get at the exif info, if for no other reason that the file may NOT be copied across from the camera in the order the pic was taken.

EDIT:

In saying that, of course when the pics are taken they are given a sequential name: DSC00001.JPG, DSC00002.JPG.

I suppose I could just use that.

---

### Post by StuartN on 2010-06-01
> **dchurch24 said:**
> they are given a sequential name: DSC00001.JPG, DSC00002.JPG.

* (or some more specific wildcard) should expand in order, so this would rename all files to a numeric:

```
x=1 ; for file in *.JPG ; do mv $file $x.JPG ; let x+=1 ; done
```

You might want mv -n or mv -i to avoid overwrites, but I assume these files are copies, not the only originals.

---

### Post by BoneKracker on 2010-06-01
> **dchurch24 said:**
> In saying that, of course when the pics are taken they are given a sequential name: DSC00001.JPG, DSC00002.JPG.

I suppose I could just use that.
:lol: 

Yes, it would seem your requirement just evaporated (assuming your camera continues numbering and doesn't restart at 1 every time you dump it, and assuming you don't add lots of other people's pictures to your collection).

---

### Post by veko on 2010-06-01
Referring to [BoneKracker]("http://ubuntuforums.org/member.php?u=64655")'s signature quote, here's a quick and simple example how go extract the date stamp from exif tag. ISO date format is naturally The Right Thing, but with back references you can really create whatever format you like.

```

#!/bin/bash
for file in *.jpg; do
    dts=`identify -verbose  $file | sed -n 's/exif:DateTime: \(.*\):\(.*\):\(.*\) \(.*\):\(.*\):\(.*\)/\1\2\3-\4\5\6/p' `
    echo $file $dts
done

```There are no error checks or anything, so this fails for example images without exif tag, file names with spaces, etc. Feel free to improve.

---

### Post by BoneKracker on 2010-06-01
Neato.  That's my favorite quote because it makes my head hurt. :P

What's that make the date/time look like?

---

### Post by dchurch24 on 2010-06-01
> **BoneKracker said:**
> :lol: 

Yes, it would seem your requirement just evaporated (assuming your camera continues numbering and doesn't restart at 1 every time you dump it, and assuming you don't add lots of other people's pictures to your collection).

The numbering starts at 000001 once the filename reaches 999999 (which, to my shame, it has done!).

@veko - thanks for that, I'll give that a try.

---

### Post by sedawk on 2010-06-01
Some comments ...


* I'm using jhead to get the exif data from a jpg file.
* I'm renaming my digital photos to something like 
  YYYYMMDD_HHMMSS.jpg
  If you have more than one jpg a second you might
  need a milliseconds or another counter (e.g. from the
  original file name) on top of the timestamp from exif.
* When knowing the sorting is right I wouldn't rely on
  numeric names of the jpg files in a loop, but
  simply iterate over the strings, e.g. reading three
  new entries, do what you want to do, read the next three
  entries, etc.

---

### Post by veko on 2010-06-01
> **dchurch24 said:**
> The numbering starts at 000001 once the filename reaches 999999 (which, to my shame, it has done!).

@veko - thanks for that, I'll give that a try.

Notice that the above script doesn't actually do anything, it just prints the file name and date stamp. But you'll easily figure out how to rename files too.

Output looks like:

imgp7579.jpg 20100118-232235
imgp7585.jpg 20100120-085655

Script is terribly slow though, I can't immediately figure out why and how to make it faster.



EDIT:
[sedawk]("http://ubuntuforums.org/member.php?u=699108")'s suggestion of using jhead is actually better solution if you just want to rename files using the date stamp.
```

jhead  -n%Y%m%d-%H%M%S  *.jpg

```will do the trick I was after in the above script.

And come to think of it, I have actually used jhead, but didn't just remember it... Oh well, forgetting things keeps you busy inventing a wheel again.

---

### Post by dchurch24 on 2010-06-01
> **veko said:**
> Oh well, forgetting things keeps you busy inventing a wheel again.

Ha - you're not wrong. I wrote a IP Listener in Python, then remembered NetCat about 6 months later!

---

### Post by dchurch24 on 2010-06-01
> **sedawk said:**
> Some comments ...


* I'm using jhead to get the exif data from a jpg file.
* I'm renaming my digital photos to something like 
  YYYYMMDD_HHMMSS.jpg
  If you have more than one jpg a second you might
  need a milliseconds or another counter (e.g. from the
  original file name) on top of the timestamp from exif.
* When knowing the sorting is right I wouldn't rely on
  numeric names of the jpg files in a loop, but
  simply iterate over the strings, e.g. reading three
  new entries, do what you want to do, read the next three
  entries, etc.

Hi, thanks for that.

....but I'm stuck ;-)

You wouldn't rely on the numeric names so, do you mean you would read them by date, three at a time?

Sorry for being thick here.

---

### Post by inameiname on 2010-06-01
I just use this python script which I put in the 'nautilus-scripts' folder, and it does the job well. However, as for your specific issue, I'm not 100% on if it'll do what you want. But I figured I'd share anyway. Who knows. Also, perhaps if you sorted by date/time in nautilus or whatever file browser first, then selected all and highlighted the oldest it would mark that one as '1.jpg', idk.

UPDATE:

Out of curiosity, I just tested my theory, of opening a folder with a bunch of files and first sorting them by 'date modified', by oldest to newest, and then right clicking the oldest and opening that script, inserting "{num1+1}.JPG", and voila, it worked just fine.

Of course, unless your file browser successfully sorts such barely noticeable older-to-younger pictures, as you said it's barely fractions of a second different, then this wouldn't work.

---

### Post by dchurch24 on 2010-06-01
Hi, thanks for that. I may well give that a go - it sounds like a good option.

However, in the meantime, if I simply take the first image, say DSC0001.JPG and increment up, then I get this:

```

#!/bin/bash
x=1;
y=0;
z=0;
while [ $x -le 350 ]  # the 350 will be the number of images in the folder, although I don't know how to get that yet.
do
  y=$(($x + 1))
  z=$(($x + 2))
  if [ $z -lt 10 ]; then
        echo "qtpfsgui -a MTB -s test$x.hdr -o /home/hdr/testhdr$x.jpg DSC0000$x.JPG DSC0000$y.JPG DSC0000$z.JPG"
  elif [ $z -lt 100 ]; then
        echo "qtpfsgui -a MTB -s test$x.hdr -o /home/hdr/testhdr$x.jpg DSC000$x.JPG DSC000$y.JPG DSC000$z.JPG"
  elif [ $z -lt 1000 ]; then
        echo "qtpfsgui -a MTB -s test$x.hdr -o /home/hdr/testhdr$x.jpg DSC00$x.JPG DSC00$y.JPG DSC00$z.JPG"
  fi
  x=$(( $x + 3 ))
done

```

---

