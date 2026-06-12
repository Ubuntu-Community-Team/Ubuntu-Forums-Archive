---
title: "How do i make the screen zoom out permanently?"
date: 2010-12-28
forum: General Help
---

### Post by a quarter past seven on 2010-12-28
how do i make the screen zoom out abit as when i open some programs or some windows pop up they are bigger than my screen and i cant read them all or click on the buttons at the bottom, ive tried resizing the boxes but they usually only expand and i can never get them to shrink,

all ive come across is things about zooming in and out but thats not really what i need,

im running ubuntu 10.10 and im on a netbook

thanks for your help

---

### Post by lungten on 2010-12-28
One option would be to use a minimal theme which uses smaller fonts with no image in buttons. They hep a lot if your screen resolution is low. Assuming you use Ubuntu check out [gnome-look]("http://gnome-look.org")

---

### Post by a quarter past seven on 2010-12-28
i dont really want to change how ive got it setup, is their no way to just make everything abit smaller so that nothing ends up being larger than my screen or a way to make the whole screen step back abit or some thing

---

### Post by lungten on 2010-12-28
> **a quarter past seven said:**
> i dont really want to change how ive got it setup, is their no way to just make everything abit smaller so that nothing ends up being larger than my screen or a way to make the whole screen step back abit or some thing

If you don't want to change anything, I wonder how you will get a different result. Perhaps, use a lens (just joking). I know of nothing like that.

---

### Post by a quarter past seven on 2010-12-28
> **lungten said:**
> If you don't want to change anything, I wonder how you will get a different result. Perhaps, use a lens (just joking). I know of nothing like that.


i see youre point ill have a look around see if theirs something else i can change to, i just thought id check see if their was something else i could do first,

im sure their was something in windows that you could use to change the ratio of the screen or something, is their nothing like that in ubuntu?

---

### Post by lungten on 2010-12-28
> **a quarter past seven said:**
> 
im sure their was something in windows that you could use to change the ratio of the screen or something, is their nothing like that in ubuntu?
If you are looking for such kind of options, then why don't you try moving your panels from top-bottom to left-right. that will give you more vertical space. but i'll feel stupid to use ubuntu that way.

---

### Post by stinkeye on 2010-12-29
You could install [**_[COLOR="DarkRed"]Ailurus [/COLOR]_**]("https://launchpad.net/~ailurus/+archive/ppa")
which provides a one click solution to reduce all your font sizes.

Alternatively you could write yourself a bash script to toggle all the changes that ailurus writes.

eg for the fonts I use, this will toggle between three font sizes down and normal.
```
#!/bin/bash

STATUS=$(gconftool-2 --get /apps/nautilus/preferences/desktop_font)

if [ "$STATUS" == "Ubuntu 11" ]; then
	gconftool-2 --set /apps/nautilus/preferences/desktop_font  --type string "Ubuntu 8"
        gconftool-2 --set /apps/metacity/general/titlebar_font  --type string "Ubuntu Bold 6"
        gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 8"
        gconftool-2 --set /desktop/gnome/interface/font_name --type string "Ubuntu 8"
        gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 7"
else
	gconftool-2 --set /apps/nautilus/preferences/desktop_font  --type string "Ubuntu 11"
        gconftool-2 --set /apps/metacity/general/titlebar_font  --type string "Ubuntu Bold 9"
        gconftool-2 --set /desktop/gnome/interface/document_font_name --type string "Sans 11"
        gconftool-2 --set /desktop/gnome/interface/font_name --type string "Ubuntu 11"
        gconftool-2 --set /desktop/gnome/interface/monospace_font_name --type string "Monospace 10"
fi
```

---

