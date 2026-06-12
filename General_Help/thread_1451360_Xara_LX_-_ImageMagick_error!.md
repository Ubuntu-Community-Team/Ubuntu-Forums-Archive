---
title: "Xara LX - ImageMagick error!"
date: 2010-04-10
forum: General Help
---

### Post by GARoss on 2010-04-10
I love Xara LX but got this error when 1st installing it;

*Xara Xtreme cannot find ImageMagick version 6.0.0 or above. Various bitmap filters will be disabled...*

I checked & found that I have ImageMagick 6.5.7 installed. I figure if I installed a pointer where the missing file should be located to where v6.5.7 is, the problem would be resolved. How can detect where the missing file should be?

---

### Post by GARoss on 2010-04-13
Well, this is weird. Basically, the warning is saying some filters will not open, but upon further review, they do. I don't get the error message but if everything is working - who cares? :)

---

### Post by liveag on 2010-06-13
Well, I still have the problem...
I, too, have imagemagick installed (v 6.5.x) but Xara doesn't seem to register it, therefore deactivating bitmap effects and the sort. I figured one could install an old version of imagemagick or make the new one appear in the places the old should, but I don't know how to do it.

Yes, I know this topic is already flagged "solved", but I hope someone will still help me.

Thanks in advance!

EDIT:
I just looked at the whereis-output for imagemagick and it doesn't seem to have a program path.```
root@peacemotion:/# whereis imagemagick
imagemagick:
```Tried reinstalling, still no luck.
Searched the internet for a possible location of the files, found [this]("http://ubuntuforums.org/showthread.php?t=611755").
It says in the linked thread that at least one function of imagemagick - convert - should be in my /usr/bin/convert.
It is not, although it is obviously installed and executable as the version output shows.
```
root@peacemotion:/bin# convert -version
Version: ImageMagick 6.5.7-8 2009-11-26 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2009 ImageMagick Studio LLC
Features: OpenMP 
```I really don't know how to fix this one.... O.o    (had the intention of making a symlink to the actually installed imagemagick from the location version 6.0 should be, but if I cant't find the files....)

---

