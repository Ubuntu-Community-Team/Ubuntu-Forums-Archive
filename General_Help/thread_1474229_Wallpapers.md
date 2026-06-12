---
title: "Wallpapers"
date: 2010-05-05
forum: General Help
---

### Post by physic.dude on 2010-05-05
I would like to toggle between 2 or more wallpapers on my 4 desktops (Compiz) with a simple hot key.

Is there a command I can add to the Compiz command settings that toggles between 2 wallpapers?

---

### Post by physic.dude on 2010-05-06
Bump

---

### Post by physic.dude on 2010-05-06
bump...
come on people...:mad:

---

### Post by WorMzy on 2010-05-06
It's not the most elegant solution, but I think this script I just wrote will do the trick for you.

```

#!/bin/bash

if [ `gconftool-2 -g /desktop/gnome/background/picture_filename` == /path/to/an/image.png ]; then
  gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/a/different/image.png";
else
  gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/an/image.png";
fi
```

Save the above to a .sh file, and make it executable. Obviously change the images in the script to what you want. When run, it will switch between the two images. Just use the Compiz "Commands" plugin to bind that command to a hotkey.

---

### Post by mechro on 2010-05-06
There's **Drapes** available via Synaptic. Once installed run **drapes** from a Terminal and it will put an icon in the notification area from which you can configure drapes.

Edit... oops, perhaps this isn't relevant re Compiz.

---

### Post by WorMzy on 2010-05-06
For more than two images, try this:
```

#!/bin/bash

currentback=`gconftool-2 -g /desktop/gnome/background/picture_filename`

case $currentback in
"/path/to/first/image.png")
  gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/second/image.png"
;;
"/path/to/second/image.png")
  gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/third/image.png"
;;
"/path/to/third/image.png")
  gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/fourth/image.png"
;;
*)
  gconftool-2 -s -t string /desktop/gnome/background/picture_filename "/path/to/first/image.png"
;;
esac
```

The final part is a default option, which will set the wallpaper to the first image if the current background image is not one of those listed in the script.

Add as many more images as you'd like, just make sure you have them correctly set out (e.g. if first image is background, switch to second; if second image, switch to third, etc).

---

### Post by physic.dude on 2010-05-07
Thanks, WorMzy
It works perfectly. 
=D>

---

### Post by WorMzy on 2010-05-07
No problem. :)

If you need any part of it explaining, feel free to ask.

---

### Post by Twexcom on 2010-05-12
I know that this isn't quite relevant, but it is convenient. You can just right click an image and click "set as wallpaper", and it does it automatically: [http://www.kompulsa.com/it/itdownloads.html#nautilus_scripts](http://www.kompulsa.com/it/itdownloads.html#nautilus_scripts)

Add that to your nautilus scripts directory.

---

