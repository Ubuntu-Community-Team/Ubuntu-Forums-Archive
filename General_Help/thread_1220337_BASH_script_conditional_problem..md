---
title: "BASH script conditional problem."
date: 2009-07-22
forum: General Help
---

### Post by JillSwift on 2009-07-22
Frankly, I have no idea why this does not work:

```
#!/bin/bash

img=/media/Music/`mpc --format [%file%] | head -1 | tail -1 | sed -e 's/\/[^/]*\..*$//' -e 's/ /\\\ /g' -e "s/'/\\\'/g"`

echo $img/cover.jpg

sel=/home/jswift/ipu.png

if [ -f $img/cover.jpg ]
then 
    sel=$img/cover.jpg
fi

if [ -f $img/cover.png ]
then 
    sel=$img/cover.png
fi

if [ -f $img/cover.gif ]
then 
    sel=$img/cover.gif
fi

echo -ne "\${image $sel -p 1,810 -s 75x75}"  

exit 0
```The conditionals are telling me "too many arguments". If I copy/paste the results into a CLI, like:
```
[ -e /media/Music/Some\ Song/cover.jpg] && echo "Y" || echo "N"
```it works. However, if I do:
```
[ -e /media/Music/`mpc --format [%file%] | head -1 | tail -1 | sed -e 's/\/[^/]*\..*$//' -e 's/ /\\\ /g' -e "s/'/\\\'/g"` ] && echo "Y" || echo "N"
```I get "too many arguments" again. :( 

Hep?

---

### Post by yabbadabbadont on 2009-07-22
Instead of using the back ticks "`" to execute the subprocess, try enclosing those commands within $().  Also, make sure to quote the result properly in case there are spaces/special characters.

e.g.  ```
[ -e "/media/Music/$(mpc --format [%file%] | head -1 | tail -1 | sed -e 's/\/[^/]*\..*$//' -e 's/ /\\\ /g' -e "s/'/\\\'/g")" ] && echo "Y" || echo "N"
```

---

### Post by JillSwift on 2009-07-22
Using $() gets me the same results. (Thanks, though, I had no idea that was an option :) )

I think I should mention that I get "too many arguments" only when there are spaces in the path - but sed is escaping those with backslashes.

---

### Post by JillSwift on 2009-07-22
Ok, I got it to work *without* escaping the spaces using sed, and just quoting the path in the conditional. Thanks for the help =^_^=

---

### Post by eightmillion on 2009-07-22
It looks to me like you need to quote your variables in your test statements. Like this:

```
if [ -f "$img/cover.jpg" ]
```

Edit: Nevermind. It looks like you figured that out.

---

### Post by Crinos512 on 2009-07-22
hmmm... try this... (changes in red)
```
#!/bin/bash

img=[COLOR="#ff0000"]"[/COLOR]/media/Music/[COLOR="Red"]"[/COLOR]`mpc --format [%file%] | head -1 | tail -1 | sed -e 's/\/[^/]*\..*$//' -e 's/ /\\\ /g' -e "s/'/\\\'/g"`
echo $img/cover.jpg

sel=[COLOR="#ff0000"]"[/COLOR]/home/jswift/ipu.png[COLOR="#ff0000"]"[/COLOR]

if [ -f $img/cover.jpg ][COLOR="#ff0000"]; [/COLOR]  then 
    sel=$img/cover.jpg
[COLOR="#ff0000"]el[/COLOR]if [ -f $img/cover.png ][COLOR="#ff0000"]; [/COLOR] then 
    sel=$img/cover.png
[COLOR="#ff0000"]el[/COLOR]if [ -f $img/cover.gif ][COLOR="#ff0000"]; [/COLOR] then 
    sel=$img/cover.gif
fi

echo -ne "\${image $sel -p 1,810 -s 75x75}"  

exit 0
```

bear in mind I do not have mpc... just playin with code. :)

---

### Post by Crinos512 on 2009-07-22
Maybe try this one as well:

**drastic rewrite**
```
#!/bin/bash

img="/media/Music/"`mpc --format [%file%] | head -1 | tail -1 | sed -e 's/\/[^/]*\..*$//' -e 's/ /\\\ /g' -e "s/'/\\\'/g"`
echo $img/cover.jpg

if [ -f $img/cover.jpg ];   then 
    echo -n "\${image $img/cover.jpg -p 1,810 -s 75x75}" 
elif [ -f $img/cover.png ]; then 
    echo -n "\${image $img/cover.png -p 1,810 -s 75x75}" 
elif [ -f $img/cover.gif ]; then 
    echo -n "\${image $img/cover.gif -p 1,810 -s 75x75}" 
else
    echo -n "\${image /home/jswift/ipu.png -p 1,810 -s 75x75}"  

exit 0
```

---

