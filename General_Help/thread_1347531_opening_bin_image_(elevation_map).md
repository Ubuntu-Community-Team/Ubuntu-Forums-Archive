---
title: "opening bin image (elevation map)"
date: 2009-12-06
forum: General Help
---

### Post by miroslav_karpis on 2009-12-06
Hi,
please can you help me with this? I have downloaded 1.1GB gz file (srtm_ramp2.world.86400x43200.bin.gz) - it should be an globe  elevation map image.

When I unzipped it I got around 6GB bin file. Does anyone know that how can I open it? (chmod 775 and running it does nothing).

I have read on web in it might be mac image format? ...don't know

---

### Post by IllegalCharacter on 2009-12-06
Where did you get it from? They should tell you there what the file format is.

---

### Post by miroslav_karpis on 2009-12-06
here is the link:
[http://visibleearth.nasa.gov/view_detail.php?id=8391](http://visibleearth.nasa.gov/view_detail.php?id=8391)

and as I can see - it does not say anything there...

---

### Post by IllegalCharacter on 2009-12-06
Try the JPG images and see if those work.

---

### Post by miroslav_karpis on 2009-12-06
that works yes,...but the resolution is lower...

---

### Post by IllegalCharacter on 2009-12-06
If they don't tell you what the image file format is, then there's not much you can do with it. You can try to guess the format type by going into a terminal (Applications->Accessories->Terminal):
```
head srtm_ramp2.world.86400x43200.bin
```
At the very start of the output you might see a code like JPG or PNG or something.

---

### Post by miroslav_karpis on 2009-12-06
that did not work. I got following output:

  		
                                                                                                                                                

---

### Post by IllegalCharacter on 2009-12-06
Unfortunately I don't know what to do for you. You should ask the people who gave it to you how to use it, since it is not a standard image file.

---

### Post by NFblaze on 2009-12-06
Try 
```

file srtm_ramp2.world.86400x43200.bin
```

to see if it will figure out the file type

---

### Post by miroslav_karpis on 2009-12-06
well...this is the output:

srtm_ramp2.world.86400x43200.bin: data

---

### Post by NFblaze on 2009-12-06
Well apparently according to that website its a BMNG bin file. Which sounds like you need a special program to open it, I would google for it

I think the programs listed here are able to open them but I am not for sure. [http://www.earthslot.org/earthslot_bmng.php]("http://www.earthslot.org/earthslot_bmng.php")

**EDIT:**
Yes, indeed you do need a special program to open it, according to the credits on that site that special program would be the 650 dollar Photoshop.
I suppose you can try it with GIMP, first be froe you shell or "acquire" photoshop.

> Open it in Photoshop but you need A LOT of memory and Version 8 or higher (e.g. I myself cannot do that): Open as -> RAW -> width 86400, height 43200 pixels, count 3, depth 8 Bits, interleaved, Header 0 Bytes.

or you can do what the reccomend here
> You would probably prefer to download the 8 PNG panels (A1-D2), as they are the same data visualized. The .bin files are the raw binary files that Reto Stockli used to generate the images in the PNG files.

via [http://visibleearth.nasa.gov/view_rec.php?id=7862]("http://visibleearth.nasa.gov/view_rec.php?id=7862")

---

### Post by blackened on 2009-12-06
Those are some seriously amazing images. 

There are JPGs of lesser resolution available on that site if you look [here]("http://visibleearth.nasa.gov/view_set.php?categoryID=2355"). I never found the PNGs though.

---

### Post by miroslav_karpis on 2009-12-06
thanks for the ideas....I have found following tool that I think I might be able to use:

[http://forum.celestialmatters.org/viewtopic.php?t=44&postdays=0&postorder=asc&start=0](http://forum.celestialmatters.org/viewtopic.php?t=44&postdays=0&postorder=asc&start=0)

---

