---
title: "script runs from terminal but not on startup"
date: 2011-07-09
forum: General Help
---

### Post by ububeginner on 2011-07-09
I want to run a script on startup that runs conky after a short delay. If I add conky directly on startup conky will always be on top of other windows until I open .conkyrc with gedit and save it again without any changes.
I'm told that this problem is caused by conky loading before the desktop is ready, so I wrote a script:
```

#!/bin/sh

sleep 9 && conky -c ~/.conkyrc && conky -c ~/.conkyForecastrc -x 250
exit 0
```

I named it .conky_start and put it in ~/

When I run it in a terminal

```
sh ~/.conky_start
```

conky will open 2 windows in 9 seconds and everything is as it should

However, if I go to System>Preferences>Startup applications and add sh ~/.conky_start
nothing seems to happen when I log back in.

---

### Post by rizzeh on 2011-07-09
when adding start up program, don't use  sh ~/.conky_start, just add full path to script without sh and ~. 
```

/home/username/.conky_start

```

---

### Post by wildmanne39 on 2011-07-09
Here is what my conky startup script looks like.
```
conky -p 40 -c ~/.conkyrc &
conky -p 40 -c ~/.conkyrc1 &
conky -p 40 -c ~/.conkyrc2 &
exit
```I just named it ssc.sh

---

### Post by ububeginner on 2011-07-09
sh /home/username/.conky_start
did the trick to run the script, thx

But it didn't solve my problem with conky beeing on top as I had hoped for, but that's another thread I guess

EDIT: Ok, I set the sleep to 20 in the script, and it did the trick, now I'll just try 15 next and experiment until I got the right sleep time

---

### Post by wildmanne39 on 2011-07-09
Hi, set it to sleep at least 40 seconds.

---

