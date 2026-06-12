---
title: "Software to scrub/delete GPS data in EXIF tags?"
date: 2012-04-17
forum: General Help
---

### Post by UnrealMiniMe on 2012-04-17
I've found several command line packages that parse EXIF tags and let you modify them piecemeal, but is there anything that actually knows what tags to look for and scrubs out anything that can be used to track or uniquely identify you?  This stuff really creeps me out, and I want it gone from my pictures without having to painstakingly figure out every single tag it could possibly be stored under (especially since there are a number of unknown tags in my images).  Heck, I wouldn't mind just nuking ALL of the EXIF data from some of these images if there were an easy way to do it. :p

You'd think this would be a pretty common functionality nowadays, but apparently not...

---

### Post by abyrne on 2012-04-17
I believe ImageMagick has the function to scrub all EXIF data. Just run this command
```
sudo apt-get install imagemagick
```
and then run this to strip your photos
```
mogrify -strip imagename.jpg
```

Source: [http://hacktux.com/read/remove/exif#imagemagick](http://hacktux.com/read/remove/exif#imagemagick)

---

### Post by UnrealMiniMe on 2012-04-17
> **abyrne said:**
> I believe ImageMagick has the function to scrub all EXIF data. Just run this command
```
sudo apt-get install imagemagick
```
and then run this to strip your photos
```
mogrify -strip imagename.jpg
```

Source: [http://hacktux.com/read/remove/exif#imagemagick](http://hacktux.com/read/remove/exif#imagemagick)

Awesome, thank you.  Taking a closer look at exiftool, it looks like it can scrub GPS data too...though it'll take some time reading the manual to get the hang of it. :p  Anyway...solved.

---

