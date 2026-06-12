---
title: "Album Art on Sansa Fuze"
date: 2009-07-04
forum: General Help
---

### Post by Bradj47 on 2009-07-04
I'm trying to get the album art to show up on my Sansa Fuze. I've tried both Amarok and EasyTAG to change it but neither worked. I decided to try eyeD3 next. At [http://eyed3.nicfit.net/](http://eyed3.nicfit.net/) it says to use this option to add images: ```
--add-image=IMG_PATH:TYPE[:DESCRIPTION]
```
I can't get anything to work with the 'TYPE' part of it. Heres what I get: 
```
brad@rockstar:/media/disk/MUSIC/AC_DC/Back In Black$ eyeD3 --add-image=31XXJ7KVAGL._SS500_.jpg "01 Hells Bells.mp3"

01 Hells Bells.mp3	[ 5.55 MB ]
-------------------------------------------------------------------------------
Time: 05:12	MPEG1, Layer III	[ ~149 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
Invalid --add-image argument: 31XXJ7KVAGL._SS500_.jpg
brad@rockstar:/media/disk/MUSIC/AC_DC/Back In Black$ eyeD3 --add-image=31XXJ7KVAGL._SS500_.jpg:jpg[:DESCRIPTION] "01 Hells Bells.mp3"

01 Hells Bells.mp3	[ 5.55 MB ]
-------------------------------------------------------------------------------
Time: 05:12	MPEG1, Layer III	[ ~149 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
Invalid APIC picture type: jpg[
brad@rockstar:/media/disk/MUSIC/AC_DC/Back In Black$ eyeD3 --add-image=31XXJ7KVAGL._SS500_.jpg:[:] "01 Hells Bells.mp3"

01 Hells Bells.mp3	[ 5.55 MB ]
-------------------------------------------------------------------------------
Time: 05:12	MPEG1, Layer III	[ ~149 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
Invalid APIC picture type: [
brad@rockstar:/media/disk/MUSIC/AC_DC/Back In Black$ eyeD3 --add-image=31XXJ7KVAGL._SS500_.jpg:: "01 Hells Bells.mp3"

01 Hells Bells.mp3	[ 5.55 MB ]
-------------------------------------------------------------------------------
Time: 05:12	MPEG1, Layer III	[ ~149 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
Invalid APIC picture type: 
brad@rockstar:/media/disk/MUSIC/AC_DC/Back In Black$ eyeD3 --add-image=31XXJ7KVAGL._SS500_.jpg:jpg: "01 Hells Bells.mp3"

01 Hells Bells.mp3	[ 5.55 MB ]
-------------------------------------------------------------------------------
Time: 05:12	MPEG1, Layer III	[ ~149 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
Invalid APIC picture type: jpg

```
What is the 'TYPE'? And if anyone knows if this won't work for modifying the album art with my Fuze, please tell how to modify it.

---

### Post by Bradj47 on 2009-07-04
This is mainly an eyeD3 question here. I'm changing the title to stop misguidance.

---

### Post by niteshifter on 2009-07-04
Hi,

This will get you TYPE info:

```
eyeD3 --list-image-types
```

Probably "FRONT_COVER" is what you want. Also, some hardware players just don't deal with ID3 tagged art, they may display small (200x200) jpeg files in a folder. Common names are Folder.jpg, AlbumArt.jpg.

---

### Post by Bradj47 on 2009-07-04
Thanks for the type info. 

> Also, some hardware players just don't deal with ID3 tagged art, they may display small (200x200) jpeg files in a folder. Common names are Folder.jpg, AlbumArt.jpg.

And I'll try renaming all the art to 'Folder.jpg'. 

Thanks!

---

### Post by Bradj47 on 2009-07-04
The Folder.jpg thing worked! I can't believe it was that simple and that I wasted all that time looking for a TAG editor that would do this when it was all as simple as renaming a file. 

Thanks again!

---

