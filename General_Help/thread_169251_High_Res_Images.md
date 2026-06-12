---
title: "High Res Images"
date: 2006-05-02
forum: General Help
---

### Post by 3david on 2006-05-02
Hi,

I'm trying to open this image:

   [http://wtc.nac.net/wtc-photo.jpg](http://wtc.nac.net/wtc-photo.jpg)

It's about 10,000x10,000 pixels (100 Mega pixel)

I tried opening it with gimp, gqview, and gliv, and they all go to 100% cpu,mem and swap
and after three-four minutes of running i kill them (after waiting about a minute until i can reach a terminal).

The two programs that managed to open it better were gThumb and IrfanView via wine.

I've been googling and trying to find linux apps designed for highres images but couldn't find any.

My system is a Dual Core Pentium 4 2.8Ghz, 512mb ram with 512mb swap.

Does anyone happen to have a better solution for high-res images on linux?

---

### Post by jazzmuzik on 2006-05-02
That's a big image. I tried opening it in Gimp and, yeah, it's super slow to open, but it did open eventually. I'm not real graphics savvy so I don't have a program suggestion for you. 

However, I did try an experiment. Since I have ImageMagick installed I converted the jpg to a tif. It's a simple matter on the command line:

convert wtc-photo.jpg wtc-photo.tif

Then I loaded the resulting tif file (44meg) in gimp. It's still slow, but about 75% faster. And zooming is nearly normal speed just like a small image.

I think the reason tif is faster is that it doesn't have to deal with decompressing the file as is the case with jpg.

---

### Post by Slim Odds on 2006-05-02
[QUOTE=jazzmuzik]I think the reason tif is faster is that it doesn't have to deal with decompressing the file as is the case with jpg.[/QUOTE]

Even your tif file is compressed, just not as much as the jpg. If you convert to a BMP (without RLE or anything like that) it's over 250 MB.

3david, this means that if the entire file is loaded into memory, it will use 1/2 of all your physical memory. And that's just the image alone.

You should look at what is already in memory and what your graphics program options/preferences are set to as far as memory allocations are concerned.

But the bottom line: that is a VERY big image. ;)

---

### Post by jazzmuzik on 2006-05-02
tif can be compressed or not. As it turns out my tif test file was compressed indicating ImageMagick's default for tif files. As you say converting it to a bmp creates a 252 meg file. I tried to open it in gimp and it won't load at all. gthumb won't touch it either. Maybe another uncompressed format would work.

I searched on "large image viewer" and found some hits for windows but not anything obvious for linux. Maybe something is out there though.

---

### Post by DoktorSeven on 2006-05-02
Hmm.  I opened it in Firefox, gqview, and Gimp -- Firefox had little to no trouble displaying it (took a bit to download though); gqview kind of stuttered a bit but showed it pretty quickly.  Neither of these really affected my system's processor load that much (memory did increase quite a bit while loading but went back down after displaying it). 

Gimp seemed to have the most trouble, taking quite a bit to open and display the image (I think mostly because it scales the image to fit the display window before displaying it) but it eventually did show it after about a minute or so.  

My system is a P41.5ghz, 384mb memory lightweight, too.  No idea why yours has so much trouble. DMA disabled on your drive, perhaps?

---

### Post by jazzmuzik on 2006-05-02
I think the convert program didn't work in my case going from jpg to bmp. There was an error somewhere in the resulting file. My system is just a bit faster, an AMD64 and 512meg RAM. DMA is enabled.

---

### Post by 3david on 2006-05-24
[QUOTE=DoktorSeven]Hmm.  I opened it in Firefox, gqview, and Gimp -- Firefox had little to no trouble displaying it (took a bit to download though); gqview kind of stuttered a bit but showed it pretty quickly.  Neither of these really affected my system's processor load that much (memory did increase quite a bit while loading but went back down after displaying it). 

Gimp seemed to have the most trouble, taking quite a bit to open and display the image (I think mostly because it scales the image to fit the display window before displaying it) but it eventually did show it after about a minute or so.  

My system is a P41.5ghz, 384mb memory lightweight, too.  No idea why yours has so much trouble. DMA disabled on your drive, perhaps?[/QUOTE]

the output of hdparm /dev/hda:
```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156301488, start = 0

```

It doesn't make sense, my firefox crashes when I try to open that file, and my system is a dual core 2.8Ghz, so why does it work so slow?

Image performance is one of the only things that bothers me on linux, images that open like nothing on windows, crash linux.
I can't even convert tiff/png files (only 1000x1000 pixels) to pdf without jumping to 100% cpu+swap+mem for 10 minutes. This is driving me crazy. :confused: any ideas?

---

