---
title: "Compressing photos for email"
date: 2006-02-26
forum: General Help
---

### Post by joris.brus on 2006-02-26
I use evolution to send email
If I want to compress pictures for email, what's the quickest way? 

using gimp to compress individual images takes too long

---

### Post by KnottyMan on 2006-02-26
jpegs are already compressed so compressing again won't accomplish much.  Do you mean you want to down scale them?

Gimp can do that as well.  I being a console guy use a chain of commands.  jpegtopnm | pnmscale | pnmtojpeg ...

---

### Post by halfvolle melk on 2006-02-26
You could install Imagemagick if you don't already have it.

Then in a terminal to the dir that contains the images.
```
cd ~/images
mkdir bla
convert -quality 50 *.jpg ./bla/images.jpg
```

This reduces the size to about 50%.

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)
[http://www.imagemagick.org/script/command-line-options.php#quality](http://www.imagemagick.org/script/command-line-options.php#quality)
and maybe compress is usefull as well, haven't tried it though.
[http://www.imagemagick.org/script/command-line-options.php#compress](http://www.imagemagick.org/script/command-line-options.php#compress)

---

### Post by joris.brus on 2006-02-26
Thanks, works like a charm

I used this command, resizing is usefull too.

 convert -quality 80 -resize 800x600 -verbose *.JPG ./bla/image.jpg

---

### Post by purpleturtle on 2006-03-26
That's great.. I've wrappered this into a little script mainly so I can do this on lots of images, and have the output filename based on the input filename.  It also does some checks so that it doesn't try to resize the image again if the output file exists, or you are trying to resize and image that has already been resized.  This is quite useful becase you can the just do "resize *.jpg" and it will only work on the files it has to!   Also it prints the file size of the output files. Hope someone finds this useful too :) 


```
#!/bin/bash

# resize : A script to resize photos suitable to be emailed etc..

readonly OUT_FMT="_med.jpg"

if [ "$#" -eq 0 ] ; then
  echo "A script to resize images suitable to be emailed etc"
  echo "Usage : $(basename $0) image1 image2 ..."
  exit 1
fi

for pic
do

  # Create the new filename
  out_name="${pic%.*}$OUT_FMT"

  if [ -e "$out_name" ] ; then
    echo "Output file $out_name exists, skipping"
  elif [ "${pic#*$OUT_FMT}" == "" ] ; then
    echo "$pic already resized, skipping"
  elif [ ! -r "$pic" ] ; then
    echo "Error : could not access $pic"
  else
    echo -n "$pic -> $out_name"
    convert -quality 80 -resize 800x600 "$pic" "$out_name"

    if [ ! -e "$out_name" ] ; then
      echo " Error .. No output file"
    else
      echo " ($(du -h "$out_name" | cut -f1))"
    fi

  fi

done

```

---

### Post by NewRubberSoul on 2006-09-30
These scripts are awesome.  Thanks a lot for posting them, you all just saved me a whole lot of time.  (what did I do before I started using linux?) :mrgreen:

---

