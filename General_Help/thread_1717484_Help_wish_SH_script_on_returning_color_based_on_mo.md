---
title: "Help wish SH script on returning color based on mouse coordinates"
date: 2011-03-29
forum: General Help
---

### Post by polardude1983 on 2011-03-29
What I am trying to do is create a script with xdotool to go to a certain coordinates, grab the color from those coordinates.

So for example it goes to coordinates 500 500 and the color it retrieves is black I want it to do one thing. If the color retrieved is not black then I want it to do something else.  I think i have all the parts but just not sure how to put it into a script

I found this page [here]("http://askubuntu.com/questions/16620/is-there-a-command-line-tool-which-returns-the-colour-of-the-pixel-based-on-scree") 

But not sure how to tell it what I want it to do.

---

### Post by polardude1983 on 2011-03-30
up

---

### Post by nice_like_rice on 2011-03-30
Why don't you take a screenshot, then grab the pixel from there, and delete the screenshot again. Not the prettiest solution, but I remember writing something a while ago that did this..

You could also try using something like python xlib, and writing a little function that uses this to take coodinates and return the colour.

---

### Post by nice_like_rice on 2011-03-30
Or use this script I just wrote.

```

#!/usr/bin/python

import Image
import sys
import os

os.system('scrot tmp.png')
im = Image.open('tmp.png')
pixel = im.load()
print pixel[int(sys.argv[1]),int(sys.argv[2])]
os.system('rm tmp.png')

```

First you must apt-get install scrot.

Usage: ./script.py x y

(scrot is a silly workaround, I don't think python has a screengrab module.)

---

