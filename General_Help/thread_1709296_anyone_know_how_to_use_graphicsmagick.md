---
title: "anyone know how to use graphicsmagick?"
date: 2011-03-18
forum: General Help
---

### Post by Arminius on 2011-03-18
trying to get it to auto crop an image in a script I'm using, script get's recycled every 10 mins, not sure if that's relevant.

```
-crop <width>x<height>{+-}<x>{+-}<y>{%}
```

and yes I've looked everywhere for an example version of what it's ment to look like when all values are entered in, having trouble with where in there your ment to put the path the image file.

all my own experiments with it haven't worked.
So anyone who has one up and running already who can provide an example for me to base my own on I would be grateful?

---

### Post by pqwoerituytrueiwoq on 2011-03-18
did you mean imagemagick?
i am not sure about auto croping
```
convert "$tmpFile" -crop "$WIDTH x $HEIGHT + $X_1 + $Y_1" +repage "$tmpFile"
```*$WIDTH* and *$HEIGHT* are size of the new image
 *$X_1* and *$Y_1* are the coordinates of where to start cropping from the top left
```
convert "mypic.jpg" -crop "25 x 50 + 100 + 30" +repage "mynewpic.jpg"
```you can overwrite the existing file with imagemagick

---

### Post by kaibob on 2011-03-18
> **Arminius said:**
> trying to get it to auto crop an image in a script I'm using, script get's recycled every 10 mins, not sure if that's relevant.

```
-crop <width>x<height>{+-}<x>{+-}<y>{%}
```

and yes I've looked everywhere for an example version of what it's ment to look like when all values are entered in, having trouble with where in there your ment to put the path the image file.

all my own experiments with it haven't worked.
So anyone who has one up and running already who can provide an example for me to base my own on I would be grateful?
The following is an example of a command line that crops the image named file.png and creates a new image named new.png. You can add a path if you want before the file names. 

```
gm convert -crop 400x200+100+50 file.png new.png
```

The new image is 400 pixels wide and 200 pixels in height; the x and y offsets from the original image are 100 and 50 pixels. Just try this command in a terminal window on a sample file to see how it works. Once you have this working, you can deal with the shell script. 

If you want to use imagemagick rather than graphicsmagick, just remove the gm at the beginning of the command line.

---

