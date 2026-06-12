---
title: "Changing wallpaper script not working"
date: 2010-06-16
forum: General Help
---

### Post by MediocreGopher on 2010-06-16
I'm running Ubuntu 10.04, and I'm having a problem using a script to randomly change my wallpaper. The script is located in a folder called Wallpapers in my home directory and executes this:

```

#!/bin/bash
#Script taken from another thread
WALLPAPERS="/home/mediocregopher/Wallpapers" #change this path for your system
ALIST=( `ls -w1 /home/mediocregopher/Wallpapers` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat $WALLPAPERS/.last` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

```Running the script in a terminal works fine. What I really want is for the script to run every 5 minutes, so I came up with this:
```

while x=0;do /home/mediocregopher/Wallpapers/.random;sleep 300;done &

```This works if I input it into the terminal by hand, but that's annoying to do, so I tried putting it into my ~/.profile file so that it would run at login. What happens is that it changes the wallpaper once as soon as I login, but then never again. I've tried the while loop in the .profile file with other commands (like zenity) and it loops through fine. Does anyone know what the problem might be?

---

### Post by inameiname on 2010-06-16
The attached script works perfectly. I actually have it set to start on startup so I have a new background at every login. And it randomly chooses one in a folder I made, ~/Pictures/Backgrounds.

And if you want a really good program, check this out:

[http://www.obfuscatepenguin.net/crebs/](http://www.obfuscatepenguin.net/crebs/)

It randomly chooses one, in a more gui manner, where you can easily set up the folder and and the time to change and all that.

---

