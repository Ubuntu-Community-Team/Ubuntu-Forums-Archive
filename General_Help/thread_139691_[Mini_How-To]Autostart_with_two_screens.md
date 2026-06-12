---
title: "[Mini How-To]Autostart with two screens"
date: 2006-03-04
forum: General Help
---

### Post by Randomskk on 2006-03-04
If you ever find you load the same programs every time; or you want your SuperKaramba or whathaveyou to load on startup, I'm sure you've played around in ~/.kde/Autostart, as any executables there get run on startup.

However, if you have two screens and run in dual head mode (ie, it's like two computers but the mouse goes between them (two framebuffers, I think)) then you'll notice that anything in the autostart gets loaded once *per screen*.
For example, if you have a link to amaroK in your Autostart folder, I guess you only want it to load once - say, on screen two - and not appear on the first screen.

By default, I can't find any options to do this, so I made my own small script.
It's really easy, and seems to work:

1) Find out your screens
Open a Konsole on both screens and type
```
echo ${DISPLAY}
``` in it, you should get something like :0.0 and :0.1

Once you know this number for each screen, take the code below:
```

#!/bin/bash
if [ "$DISPLAY" = "screennumber" ]; then
        exec /usr/bin/program
fi

```
And change "screennumber" to the number of the screen you want it to load on, and change program (or /usr/bin/program if the bin isn't there) to point to what program you want.
Then, save it as something like "program.sh" in your ~/.kde/Autostart, and in a konsole type "chmod +x program.sh".

For example, my script to load amarok on the second screen:
```

#!/bin/bash
if [ "$DISPLAY" = ":0.1" ]; then
        exec /usr/bin/amarok
fi

```

You could have it load multiple things per script (add a " &" after the program path, then the next program a line below) or just have a script per program.

---

