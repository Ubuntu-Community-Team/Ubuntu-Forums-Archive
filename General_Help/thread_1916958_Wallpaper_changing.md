---
title: "Wallpaper changing"
date: 2012-01-29
forum: General Help
---

### Post by Theredbaron1834 on 2012-01-29
Say I have an image file that updates every once in a while. Like a static web cam. Is there any way I can monitor the file, and when it changes set it as my desktop (PCmanFM) wallpaper? I Don't want to just run a script that does it every * min. Waste time/resources when/if it doesn't change. (Every 3 min for a while, then nothing for hours/days.)

Lubuntu 11.10 x64

---

### Post by Rodney9 on 2012-01-29
This will change your wallpaper periodically 

[http://ubuntuforums.org/showthread.php?t=1843824](http://ubuntuforums.org/showthread.php?t=1843824)

I know that's not what you want.

You need someone clever with scripts to combine the above with watch or tail.



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Theredbaron1834 on 2012-01-29
:), I use that thread all the time. :) Very nice.

And thanks, Never even heard of the watch command before, not a big CL person. Going to try and use it myself, don't know if I can, but will try.

So, I did a little research, and sorta got one started. Though I didn't use the watch command, just du and if test then
```
#/bin/bash

z2=0

while :

do
    z1=$(du /path/to/image.png | head -c 3)
    if test [$z1 != $z2]; then 
        pcmanfm --set-wallpaper=/path/to/image.png
        sleep 120

        fi
    z2=$(du /path/to/image.png | head -c 3)
    sleep 10
done
```But it is never equal, even when it should. As I said, not good as scripts, first time trying variables, so I am sure it is just my stupidity.

Any help?

Well, I got it figgered out. Here is the working code for anyone
```
#/bin/bash
while :

do
    z1=$(du /path/to/image.png | head -c 3) # set z1 as the first 3 numbers in a filesize
    if test $z1 -ne $z2; then
        pcmanfm --set-wallpaper=/path/to/image.png
        z2=$(du /path/to/image.png | head -c 3) # set z2 as the first 3 numbers in a filesize    
        sleep 120
        else
        z2=$(du /path/to/image.png | head -c 3)  # set z2 as the first 3 numbers in a filesize
    sleep 5
        fi
done
```Not pretty, I am sure, but it works.

---

