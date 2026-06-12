---
title: "lots of pngs -&gt; animated gif, how?"
date: 2010-04-08
forum: General Help
---

### Post by nbv4 on 2010-04-08
I have a folder with a ton of png files, all names based on a date: 2010-01-03.png, 2010-01-01.png, etc. I want to take all of these images and make them animated. Whats the easiest way to do this? It really doesn't even need to be a gif, any animated format will do.

---

### Post by dominiquec on 2010-04-08
Install ImageMagick.

```
sudo apt-get install imagemagick
```

Then on your files run:

```
convert -delay 20 -loop 0   *.png  myanimation.gif
```

---

### Post by dominiquec on 2010-04-08
By the way, please back up your files before you try the command.  Don't want to be responsible for messing up your images.

---

### Post by SnickerSnack on 2010-04-08
You might end up having to rename the images so that they're in the order you want them in.

I believe that GIMP (import sequential image files as a gif) will do this too, so if you already have it, you might it as well, though I wouldn't recommend installing it just for that purpose.

---

### Post by nbv4 on 2010-04-08
Actually I found a better solution: [http://pastebin.com/Rr7dAxbF](http://pastebin.com/Rr7dAxbF)

So I can just do this:

```

$ wget http://pastebin.com/download.php?i=Rr7dAxbF -O images2gif.py
$ python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from images2gif import glob2Gif
>>> glob2gif('/home/chris/images/*.png', 'out.png', duration=0.1)
91 frames written

```

it's not a perfect solution, but eh works well enough

---

