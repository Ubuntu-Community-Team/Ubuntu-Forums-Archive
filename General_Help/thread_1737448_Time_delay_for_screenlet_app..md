---
title: "Time delay for screenlet app."
date: 2011-04-23
forum: General Help
---

### Post by Chrysalids on 2011-04-23
Hello, first off I am sorry if I am in the wrong place.  I am about 2 days old using Ubuntu.  I started off using open source software and decided to try Linux on my other machine. So far loving it. I am still stunned this is free to download, I was not expecting so much eye candy :).

Ok my question, I was looking for a calender and weather app for the desktop.  I have always ran them as I use them both quite often.  I found from much reading some ides and liked screen-lets.  The calender works great but the weather will open but never update.  This machine is wireless so I think what is happening is that there is no connection for at least 5 to 8 sec, I was hoping there was a way to have the one app (clear weather) open on a delayed timer so I don't have to keep right clicking and choosing zip code to connect and get the update.  I have seen some things, like script that have the word bash in it but was hoping for a site that maybe my search parameters are failing to find on how to do this.  

Thank you for your time.

---

### Post by Chrysalids on 2011-04-23
Was hoping if someone could assist with this problem.  I am still searching in the meantime.

---

### Post by Baumbart on 2011-04-23
I had that with conky but I don't know if the solution is transferable:

Write a shell

#!/bin/bash
sleep 10
APPNAME
exit 0

name it *somename.sh* and add it to the start-programs instead of the app.

Please tell me if it works.

EDIT: Now I see you have already found such a solution

---

### Post by Chrysalids on 2011-04-23
Thanks for the help, I actually ended up using this command I found on an older post.  Just using bad search parameters on my part.  I used.

```
bash -c "sleep 20; python -u /usr/share/screenlets/screenlets-pack-basic/ClearWeather/ClearWeatherScreenlet.py"
```

This resolved my issue but I will keep what you showed also, one less search down the road :).

---

