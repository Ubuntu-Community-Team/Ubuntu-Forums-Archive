---
title: "Shell script .. How to find images and replace them ?"
date: 2009-08-30
forum: General Help
---

### Post by credobyte on 2009-08-30
I need a way to find all start-here-kde.png images in /usr/share/icons ( recursively ) and replace them with a custom image ( eg., located at my Desktop ).
How would I do that ( my shell scripting knowledge is below zero ) ?

Here's an example! It found images & now I need to replace them with another image: /home/skywalker/start-here-kde.png ..
```
skywalker@ubuntu:~$ find /usr/share/icons -name "start-here-kde.png"
/usr/share/icons/oxygen/64x64/places/start-here-kde.png
/usr/share/icons/oxygen/22x22/places/start-here-kde.png
/usr/share/icons/oxygen/128x128/places/start-here-kde.png
/usr/share/icons/oxygen/48x48/places/start-here-kde.png
/usr/share/icons/oxygen/16x16/places/start-here-kde.png
/usr/share/icons/oxygen/32x32/places/start-here-kde.png
```

---

### Post by PGScooter on 2009-08-30
you could try this, but I am not sure it will work so back everything up:

```
find /usr/share/icons -name *"start-here-kde.png" -exec mv /path/to/your/image.png '{}' \;
```

This will use image.png and replace all of the entries that find finds. Is that what you want?

---

### Post by credobyte on 2009-08-30
> **PGScooter said:**
> you could try this, but I am not sure it will work so back everything up:

```
find /usr/share/icons -name *"start-here-kde.png" -exec mv /path/to/your/image.png '{}' \;
```This will use image.png and replace all of the entries that find finds. Is that what you want?

Yes, that's exactly what I needed, except .. mv should be replaced with cp ( otherwise, I need a lot of images :D ). Thank you!

---

### Post by PGScooter on 2009-08-30
> **credobyte said:**
> Yes, that's exactly what I needed, except .. mv should be replaced with cp ( otherwise, I need a lot of images :D ). Thank you!

ah, good point! To be safe, you could also use -i with cp so that it should ask you each time before overwriting.

---

### Post by credobyte on 2009-08-30
> **PGScooter said:**
> ah, good point! To be safe, you could also use -i with cp so that it should ask you each time before overwriting.

Nah, that's and old machine, sitting in the corner and waiting for me to screw something up ( only for testing purposes ) ;)

---

