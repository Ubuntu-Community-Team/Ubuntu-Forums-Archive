---
title: "Exporting with Inkscape from command line"
date: 2006-04-20
forum: General Help
---

### Post by Jong on 2006-04-20
I'm trying to use Inkscape for exporting SVG files to PNG files. However I have yet to figure out how to export more than one file at a time from the command line.

The following command exports a single file:
inkscape filename.svg --export-png=filename.png

How do I export all files within a directory?

---

### Post by ertz on 2008-05-27
Save this code as an exectuable text file in ~/.gnome2/nautilus-scripts

```

#!/bin/bash
#
# Copyright 2007 Silvestre Herrera <silvestre.herrera@gmail.com>
# Available under the terms of the GNU GPL.
#
# Convert everything to PNG
# This one is a must have if you're developing a PNG theme
# or if you're just resizing SVGs and exporting them as PNGs.

mkdir SVGs

for i in *.svg; do
	inkscape $i --export-png `basename $i .svg`".png"
	mv $i SVGs/
done

```

Then, in nautilus, you can access the script in "right click" > Scripts

---

### Post by Ro_han on 2008-07-10
I have a similar problem in that I have a directory of svg files and I want an automated program to convert each svg file into several png files of different predefined sizes (stretching the svg). I'd prefer this to opening Inkscape and resizing every svg by hand then exporting them one at a time.

If someone had a script for just converting one svg into several png files of different sizes I could figure out how to generalise it for an entire dir.

Thanks.

---

