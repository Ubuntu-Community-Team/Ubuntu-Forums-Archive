---
title: "Batch Image Convert from PNG to JPG fails"
date: 2010-09-28
forum: General Help
---

### Post by Vigh on 2010-09-28
convert "$fractal.png" "$fractal.jpg"
convert: unable to open image `.png':  @ error/blob.c/OpenBlob/2498.
convert: no decode delegate for this image format `.png' @ error/constitute.c/ReadImage/532.
convert: missing an image filename `.jpg' @ error/convert.c/ConvertImageCommand/2970.

How can I fix this error and batch convert images in the terminal.
Regards

---

### Post by WorMzy on 2010-09-28
Use the following command:

```
for img in *.png; do convert $img $img.jpg; done
```

If you want a specific quality, do

```
for img in *.png; do convert -quality [COLOR="Red"]50[/COLOR] $img $img.jpg; done
```

More arguments can be found by running
```
man convert
```

Oh, and you can get rid of the superfluous extension with

```
for img in *.jpg; do mv $img `echo $img | sed 's/.png//'`; done
```

You could probably merge the two commands into one, but I prefer to keep them separate.


Oh, you need imagemagick installed for the convert command to work. So run

```
sudo apt-get install imagemagick
```

if you get "command not found".

---

### Post by Vigh on 2010-09-28
okay seems to have worked but I have one very serious question here!!! how is it magic??? it converted 22,019 images in the space of a single second?!?!?! how is that possible!

lol my bad, its still processing

thanks for your help,
another question, will it delete the originals? I would prefer this, as 6GB is too much space to waste

---

### Post by WorMzy on 2010-09-28
I'd be very impressed if it was that quick. :p

It won't delete the originals, but you can run

```
for img in *.png; do rm $img; done
```

to delete the .pngs afterwards. If I'd known that you wanted to delete the originals to begin with, I'd have added the "rm $img" to the original command, so that it removed each original after it'd converted it to jpg:

```
for img in *.png; do convert $img $img.jpg [COLOR="Red"]&& rm $img[/COLOR]; done
```

However, now that you're already running the command, it'd be best to let it finish, or else you'll have half converted, and half unconverted. You could delete all the .jpgs and start again with the new command if you want though. Pressing Ctrl+C will cancel the running command (if it's still going)

---

### Post by WorMzy on 2010-09-28
Bump for updated post.

---

### Post by Vigh on 2010-09-28
cool thanks, also learnt a key thing!!! dont rely on nautilus for moving 20,000+ files around at a time, need to use the mv command in terminal! Otherwise CPU usuage = 100% and takes ages to move the files.

---

