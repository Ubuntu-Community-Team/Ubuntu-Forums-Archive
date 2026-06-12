---
title: "RAW Image Conversion"
date: 2011-07-19
forum: General Help
---

### Post by Khakilang on 2011-07-19
I was shooting an event recently and end with over 4000 images in RAW format. And I am trying to convert all the RAW image to Jpeg in batches. But all I got is small Jpeg size file which is only about 800KB in size. But what I really want is to be able to convert into large Jpeg files something like 5 or 6MB Jpeg file. I have use Picasa and Shotwell but both only give me small Jpeg file. So the question is whether there is any software that can export RAW image file to large Jpeg file in batches? I am not going to use GIMP to convert one by one. That will take ages. I just need a software to convert the whole lot. Thank to anyone who reply.
:popcorn:

---

### Post by undecim on 2011-07-19
imagemagick will do it

Open a terminal, go to the directory with your .raw's, and run this: 

```
find -iname \*.raw -exec sh -c 'convert {} `basename {} .raw`.jpeg' \;
```

each of your .raw's now has a .jpeg brother.

---

### Post by eric-yorba on 2011-07-19
Khakilang, there is no such thing as "converting" from a RAW to a JPEG -- RAW files (generally) contain more color information than a JPEG.  Any RAW file will take a bit of tweaking to get a good looking JPEG out of it.

As for programs that can process RAW files in batch, you might have a look at RawTherapee or Ufraw, both of which are in the Ubuntu repositories.  I couldn't tell you off the top of my head if Ufraw has batch support, but RawTherapee definitely does.

---

### Post by ssam on 2011-07-19
i use the following script when i want to quickly develop a batch of raws.
```

#!/bin/bash
echo "making full size jpegs from all *.crw and *.cr2 files in directory"

RAW2PPM="dcraw -v -w -n 20"
PPM2JPEG="convert -quality 90"

mkdir jpeg

for file in *.(crw|CRW|cr2|CR2)
do
    #make names
    fileppm=`echo $file | sed "s/[Cc][Rr][Ww2]$/ppm/"`
    filejpeg=`echo $file | sed "s/[Cc][Rr][Ww2]$/jpeg/"`

    echo $file $filejpeg $fileppm   

    $RAW2PPM $file
    echo converting to $filejpeg
    $PPM2JPEG $fileppm jpeg/$filejpeg

    #delete halfway step
    rm $fileppm
    echo $file done
done

```

you can tweak the dcraw options if you need.

Something like rawtherapee or rawstudio is better if you want more control.

---

### Post by jcolyn on 2011-07-19
Rawstudio does batch processing and is a very good program..

---

### Post by Khakilang on 2011-07-19
Currently I am using Picasa to do mass image processing. Like "Auto Contrast" and "Auto Colour". Than I use export to Jpeg. But it only give small Jpeg files. I have try Adobe Photoshop Lightroom that give large Jpeg files and it work. Maybe I'll have a look at RAWStudio and RAWtherapee. Thank for all your respond!

---

### Post by Wim Sturkenboom on 2011-07-20
ufraw-batch (part of ufraw)

e.g.
```

ufraw-batch *.PEF

```
Obviously replace PEF by the extension that your camera uses ;)

---

### Post by Khakilang on 2011-07-21
Ok! I have install RAWStudion and RAWTherapee. Its seem this is what I am looking for. Thank you guys for all the respond.

---

