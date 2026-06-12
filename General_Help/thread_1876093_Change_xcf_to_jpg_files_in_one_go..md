---
title: "Change xcf to jpg files in one go."
date: 2011-11-05
forum: General Help
---

### Post by BlackS3th on 2011-11-05
Hello Linux comrades!

I have a file full of xcf (gimp format). And i want to change them all to jpg at once (cause there are to many file's, im working on something) and it would take too much time to convert 1 by 1... Any help as which command should i use?

Cheers :D

---

### Post by hwttdz on 2011-11-05
Seems like imagemagick should do the trick.

convert -flatten inputfile outputfile

or for all files in directory (and subdirectories)

find . -type f -name "*.xcf" -print0|perl -pe 's/\.xcf//'|xargs --null -I{} bash -c "convert -flatten {}.xcf {}.jpg"

or change jpg to whatever format you want.

---

### Post by BlackS3th on 2011-11-05
ive tryied find . -type f -name "*.xcf" -print0|perl -pe 's/\.xcf//'|xargs --null -I{} bash -c "convert -flatten {}.xcf {}.jpg" but it was unable to do anything to jpg... and i didnt quite understood what should i type in convert -flatten inputfile outputfile... :(


also the path to the file is that

'/home/user/&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;/The Black sand/Practice/2nd attemt'

---

### Post by hwttdz on 2011-11-05
Yeah, that didn't work because I tried to use the null separation passing through perl in the middle.  But it wouldn't have worked even given that because imagemagick and gimp can't get along on xcf and transparency, so now 2 part solution.

First grab a copy of xcftools from the repository.  Then we convert xcf to png.

find . -name "*.xcf" --null|perl -pe 's/\.xcf//;s/(.*)/$1.xcf > $1.png/'|xargs --null -n 1 -I{} -t bash -c "xcf2png -b white {}"

then we convert png to jpg

find . -name "*.png" --null|perl -pe 's/\.png//;s/(.*)/$1.png $1.jpg/'|xargs --null -n 1 -I{} -t bash -c "convert {}"

sidenote 1: The best way of doing this would be with a gimp script, but that looks annoying at the moment.
sidenote 2: not having spaces in file names or paths makes this a fair bit easier.

---

### Post by VCoolio on 2011-11-05
I'm not sure about the difficult perl stuff. Isn't this the same:```
for i in $(ls | grep xcf); do xcf2png $i ${i%.xcf}.png; done
for i in $(ls | grep png); do convert $i ${i%.png}.jpg; done
```

---

### Post by llamabr on 2011-11-05
Also, if you want imagemagick, it will do batch stuff by itself with mogrify:

[http://www.imagemagick.org/www/mogrify.html](http://www.imagemagick.org/www/mogrify.html)

---

### Post by BlackS3th on 2011-11-06
find: unknown predicate `--null'
from the terminal...

:(

---

### Post by hwttdz on 2011-11-06
Sorry, the null in the find should be -print0

```
find . -name "*.xcf" -print0|perl -pe 's/\.xcf//;s/(.*)/$1.xcf > $1.png/'|xargs --null -n 1 -I{} -t bash -c "xcf2png -b white {}"
find . -name "*.png" -print0|perl -pe 's/\.png//;s/(.*)/$1.png $1.jpg/'|xargs --null -n 1 -I{} -t bash -c "convert {}"
```

VCoolio, yes the two are the same assuming no spaces in filenames, the print0 gets you null separated output, and the --null in xargs tells xargs to use nulls to separate arguments which bypasses the spaces in filenames issue (at a lot of added complexity granted, but I saw the OP has spaces in paths and filenames).

---

