---
title: "Apache2 Not Serving Images beginning with number..."
date: 2012-04-05
forum: General Help
---

### Post by wapitismith on 2012-04-05
I'm not sure where to start.  I have created a tile server through mapnik and the tiles are placed in a hierarchy of ```
../6/13/25.png
``` 

I can follow the index through the browser down to the image, and then I get a "404 Not Found The requested URL /osm/6/13/23.png was not found on this server."  I've checked and changed the permissions to 777 and that doesn't work.  for the tile server to work properly, the file is contained in directories that represent```
 /{scale}/{x-tile}/{y-tile}.png
```

I've used imagemagick to convert to other formats thinking it may correct small anomalies in the image (which I can open in any image viewer) but I still can not open if the file name begins with a number.  if I change the file name to add a character (other than a number) to the beginning 'a23.png' it is view-able,
but '23a.png' is not.

What am I doing wrong?

---

### Post by wapitismith on 2012-04-05
Okay, this is strange (well, at least to me) but if I double slash the last slash i.e. ```
'../6/13//24.png'
``` the image displays.  ```
'../6/13\/24.png'
``` also works.

If I move the tiles to a new directory, they will serve.  But I can't find anything that limits the access in the original directory...

Is there a setting in the Apache2 conf files I'm missing?

---

