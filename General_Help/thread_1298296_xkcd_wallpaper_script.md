---
title: "xkcd wallpaper script"
date: 2009-10-22
forum: General Help
---

### Post by mikeglover on 2009-10-22
Anyone know how to make a script that will download the latest xkcd comic and set it as the desktop wallpaper for that day?

[http://xkcd.com/](http://xkcd.com/)

Cheers,

---

### Post by Simian Man on 2009-10-22
It shouldn't be that hard.  If nobody responds by tomorrow, and I get bored, I will give it a go :).

---

### Post by diesch on 2009-10-22
```
#!/bin/sh
FILE=$HOME/wallpaper.png

wget -q -O "$FILE" "$(wget -q -O- http://xkcd.com/| egrep -o 'http://imgs\.xkcd\.com/comics/.+?\.png'|head -n1)" && ( gconftool-2 --type str --set /desktop/gnome/background/picture_filename "$FILE"; gconftool-2 --type str --set /desktop/gnome/background/picture_options "scaled" ) 

```

---

### Post by zivley on 2009-10-22
> **diesch said:**
> ```
#!/bin/sh
FILE=$HOME/wallpaper.png

wget -q -O "$FILE" "$(wget -q -O- http://xkcd.com/| egrep -o 'http://imgs\.xkcd\.com/comics/.+?\.png'|head -n1)" && ( gconftool-2 --type str --set /desktop/gnome/background/picture_filename "$FILE"; gconftool-2 --type str --set /desktop/gnome/background/picture_options "scaled" ) 

```

Darn, you type faster than me!
I was about to post the same solution!
Great minds think alike...

Now he only needs to set a schedule for it to run daily

---

### Post by mikeglover on 2009-10-22
Thanks all :-)

---

### Post by mikeglover on 2009-10-23
Tried the script but get this:
```
/home/mike/wallpaper.png: Permission denied
```

Tried it as root but the wallpaper does not change.

When I get the script I hope to use anacrontab to automate the script. Can someone tell me how I would do it?

---

### Post by mikeglover on 2009-10-23
Fixed the error.

Just need to know how I can use anacrontab to refresh this every day?

---

### Post by t0p on 2009-10-23
> **mikeglover said:**
> Fixed the error.

What did you do?

> **mikeglover said:**
> 
Just need to know how I can use anacrontab to refresh this every day?

First of all run the command:

```
crontab -e
```This opens a file in default editor (vim unless you change it)

Add a line like this:

```

[FONT=Times New Roman][SIZE=3]*     9     *     *     *         /path/to/your/script
[/SIZE][/FONT]
```[FONT=Times New Roman][SIZE=3]

That example would run the script once a day at 9.00 AM. [/SIZE][/FONT]

---

### Post by doas777 on 2009-10-23
I've seen variations on that script before (and i use a simmilar principal in my python manga scraper) but the thing that bothers me about it specifically for XKCD, is that you miss the mouse-overs which are often one of the funniest parts.

---

### Post by Jayferd on 2009-10-23
With a little more egrep and imagemagick work you could, i suppose, get the alt text to appear in the image; or download it into a text file on the desktop.

Also, since I'm one of those weird people who actually turns off their computers when they're not using them, I would probably set this script to run at startup.

---

### Post by diesch on 2009-10-23
```
#!/bin/sh

TMPDIR=$(mktemp -d /tmp/xkcdXXXXXXXXXX)
HTML="$TMPDIR/html"
PNG="$TMPDIR/xkcd.png"

DEST="$HOME/xkcd_wallpaper.png"


wget -q -O- http://xkcd.com/|egrep  '<img src="http://imgs\.xkcd\.com/comics/.+?\.png"' > "$HTML"

URL=$(cut -d\" -f2 "$HTML")
TITLE=$(cut -d\" -f4 "$HTML")

wget -q -O "$PNG" "$URL"

WIDTH=$(identify -format '%w' "$PNG")

convert "$PNG"  -background '#0008' -fill white -gravity Center -pointsize 30 -size "${WIDTH}x200" caption:"$TITLE" -append "$DEST"

rm -r "$TMPDIR"

gconftool-2 --type str --set /desktop/gnome/background/picture_filename "$DEST"
gconftool-2 --type str --set /desktop/gnome/background/picture_options "scaled"

```


The convert call needs some more work to make the text look good

---

### Post by diesch on 2009-11-06
A version with some bugfixes is available at [http://www.florian-diesch.de/software/shell-scripts/#xkcddesktop](http://www.florian-diesch.de/software/shell-scripts/#xkcddesktop)

---

### Post by abumaia on 2010-07-18
How would you modify this to not set the image as a wallpaper, but just an image on the desktop, like a screenlet?

---

