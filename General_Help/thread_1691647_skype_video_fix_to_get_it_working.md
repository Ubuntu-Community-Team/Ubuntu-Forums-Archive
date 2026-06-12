---
title: "skype video fix to get it working"
date: 2011-02-20
forum: General Help
---

### Post by sdowney717 on 2011-02-20
It works now following this
[http://forum.skype.com/index.php?showtopic=144791](http://forum.skype.com/index.php?showtopic=144791).

> How to launch Skype + V4L2 directly from Gnome/Ubuntu Jaunty menus so that the webcam works:
Menu System --> Preferences --> Main Menu
In the window select Internet, then Skype
Click on [Properties] button
In Command enter this exacly as shown:
it used to say skype-wrapper

bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'


It makes me wonder if skype-wrapper in the command line would have worked as I always was starting it from terminal

---

### Post by sdowney717 on 2011-02-20
I did notice in that field for command line this text for file skype-wrapper found in usr/bin


#!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
mkdir -p ~/.Skype
cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"

I suppose you could make it say this and it would work with skyp-wrapper
bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype' 

WHY NOT get this fix into the release? OR is this totally under the control of skype?

---

