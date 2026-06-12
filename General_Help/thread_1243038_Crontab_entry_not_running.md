---
title: "Crontab entry not running"
date: 2009-08-17
forum: General Help
---

### Post by j.bell730 on 2009-08-17
I've set up a crontab entry using
```
crontab -e
```

The entry looks like this
```
0,5,10,15,20,25,30,35,40,45,50,55 * * * * sh /home/jared/wallpapers.sh
```

In my home directory, there is a custom bash script, which is intended to pick a random wallpaper. The script looks like this
```
#!/bin/bash

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$(ls ~/Pictures/ccy/Jessica\ Alba/* | shuf -n1)"
```

(The above commands and scripts are the only things I've done that are relevant to this, except for a reload of cron, but I don't think that's important.)
This script runs great when I run it from a bash prompt. However, it's not running as scheduled via cron.
I've just started exploring the system more to increase my knowledge of the customisability of Linux, so I'm not really knowledgeable about this. There's probably a command I'm missing to activate it or some type of configuration I need...I can't be sure. Also, as such, I'd prefer to do this the way I've posted, just so I can say I did it :P.

Any help is much appreciated. Thanks.

EDIT- Oh, yeah, and the script is executable.

---

### Post by wojox on 2009-08-17
```
*/5 * * * * sh /home/jared/wallpapers.sh
```

Every five minutes right?

---

### Post by j.bell730 on 2009-08-17
Yes, thanks! It works now.

---

