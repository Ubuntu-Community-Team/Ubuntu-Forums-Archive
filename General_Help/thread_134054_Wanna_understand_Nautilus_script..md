---
title: "Wanna understand Nautilus script."
date: 2006-02-21
forum: General Help
---

### Post by Owdy on 2006-02-21
I found this script. I wanna learn to understand these scripts. What is engine behind that image size conversion? ImageMagic or what? :)


```
#!/bin/bash
title="Pienennä kuvan kokoa"
scale="Kutista kokoon <pituus>x<korkeus>"

case $LANG in
    sv* )
        title="Skala bild"
        scale="Storlek att skala till <längd>x<höjd>";;
esac

imgsize=`gdialog --title "$title" --inputbox "$scale" 200 100 2>&1`

while [ $# -gt 0 ]; do
    picture=$1
    /usr/bin/convert -scale $imgsize "$picture" "$imgsize-$picture"
    shift
done
```

---

### Post by halfvolle melk on 2006-02-21
Hi,

That's a Bash script. Can't really help you with that because I've only just started looking into it myself, but you could start here:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

And here's the rest of my Bash bookmarks:
[http://tlgp.sourceforge.net/Bash-Beginners-Guide/](http://tlgp.sourceforge.net/Bash-Beginners-Guide/)
[http://floppix.ccai.com/scripts1.html](http://floppix.ccai.com/scripts1.html)
[http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html](http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by ow50 on 2006-02-21
```
#!/bin/bash
```
Bash script as  mentioned above.

```
title="Pienennä kuvan kokoa"
scale="Kutista kokoon <pituus>x<korkeus>"
```
Variable definitions.

```
case $LANG in
    sv* )
        title="Skala bild"
        scale="Storlek att skala till <längd>x<höjd>";;
esac
```
Internationalization.

```
imgsize=`gdialog --title "$title" --inputbox "$scale" 200 100 2>&1`
```
Get size from a dialog. Uses zenity. See "man zenity" for details, gdialog is probably deprecated.

```
while [ $# -gt 0 ]; do
    picture=$1
    /usr/bin/convert -scale $imgsize "$picture" "$imgsize-$picture"
    shift
done
```
I'm not that familiar with bash, but if this works right it should process all files given as arguments saving the scaled versions with a filename prefixed with the imagesize. convert is one of the imagemagick scripts. See "man convert" and "man imagemagick".

I have written a script almost identical, except for using zenity directly and using a different looping style.
```
#!/bin/bash

# Resize selected image files.

size=`zenity \
	--entry \
	--title "Create thumbnails" \
	--text "Biggest thumbnail dimension (pixels)"`

if [ $size = "" ]; then
	exit 0
fi

for arg; do
	convert -size "${size}x${size}" -resize "${size}x${size}" "$arg" "tn-$arg"
done

```

---

### Post by Owdy on 2006-02-21
Thanks so far. Isnt that my script use ImageMagic?

---

### Post by engla on 2006-02-21
[QUOTE=Owdy]Thanks so far. Isnt that my script use ImageMagic?[/QUOTE]
yes, 'convert' is a tool that comes with ImageMagick

---

