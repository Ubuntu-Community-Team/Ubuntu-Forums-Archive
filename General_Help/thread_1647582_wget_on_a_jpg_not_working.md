---
title: "wget on a jpg not working"
date: 2010-12-17
forum: General Help
---

### Post by Affrikka on 2010-12-17
Hey everyone,

I am trying to have this cool effect where gnome scheduler downloads with wget [this image](http://static.die.net/earth/mercator/1600.jpg) every three hours.
However, even when I do it manually in the terminal it doesn't seem to download it correctly. When I go to open the .jpg it says in a big red bar on the top "Could not load image '1600.jpg'. Error interpreting JPEG image file (Not a JPEG file: starts with 0x47 0x49)"

However, when I go to the picture in the link above and right click "Save Image As" it downloads it fine.

Any reason this could be?

thanks!

Mathieux

---

### Post by TSJason on 2010-12-17
Mathieux,

The webmaster is blocking unknown or specifically the wget user-agent; so just specify a different one. For instance I'm using google chrome here:


```
wget -O 1600.jpg --user-agent="Mozilla/5.0 (X11; U; Linux x86_64; en-US) AppleWebKit/534.10 (KHTML, like Gecko) Chrome/8.0.552.224 Safari/534.10" http://static.die.net/earth/mercator/1600.jpg

```

---

### Post by Affrikka on 2010-12-17
oh okay, thank you so much! everything works fine now!

---

### Post by doperative on 2010-12-17
> **Affrikka said:**
> When I go to open the .jpg it says in a big red bar on the top "Could not load image '1600.jpg'. Error interpreting JPEG image file (Not a JPEG file: starts with 0x47 0x49)" However, when I go to the picture in the link above and right click "Save Image As" it downloads it fine
Wget downloads it here, what's curious is that using Imagemagic->Display it only displays for less than a second, how is this achieved?

---

### Post by TSJason on 2010-12-17
It looks like it's actually sending an animated gif format file when the wget user-agent is used. 

Interesting....I wonder if this is for a specialized auto-refresh system?

---

