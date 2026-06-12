---
title: "Rename movie files to creation date/time"
date: 2012-02-09
forum: General Help
---

### Post by ufis on 2012-02-09
I have several short movie clips from my cellphone (.3gp) that I wish to rename based on the date/time it was created.

For all my images I have found
```
exiv2 -F rename -r "%Y%m%d_%H%m" *.jpg
```
to perform that task, but I cannot seem to find something similar for the movie files.

Any help?

PS. Using ubuntu 10.04 if that makes any difference

---

### Post by Khayyam on 2012-02-09
ufis ..

exif2 doesn't support 3gp metadata, [exiftool](http://www.sno.phy.queensu.ca/~phil/exiftool/) does however.

3gp (as with mp4) stores its timestamp as seconds from '1904-01-01 00:00:00' which means that some voodoo is necessary to convert that format into '%Y%m%d_%h%m'. Whether exiftool does this I'm not sure, but it can read the metadata and so that information could be extracted and manipulated to provide creation time in human format.

There is some useful information, scripts, etc on the [Gentoo Linux Wiki](http://www.gentoo-wiki.info/TIP_Organizing_digital_photos) that might be of some help if you can't find an example similar to your exif2 command via google.

HTH ...

Major_Bloodnok .. that is not very useful at all.

---

### Post by ufis on 2012-02-15
Thanks. I will look into it and post here if I get it right.

---

