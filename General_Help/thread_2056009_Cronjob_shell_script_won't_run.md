---
title: "Cronjob shell script won't run"
date: 2012-09-10
forum: General Help
---

### Post by natespaceorama on 2012-09-10
I have this script and cronjob set up, but for some reason it won't run. The script is executable and works just fine when I run it manually, but doesn't run with the cronjob. I've checked everything I can think of and still have no idea what's wrong.

[http://i.imgur.com/JjQJO.png](http://i.imgur.com/JjQJO.png)

---

### Post by Cheesemill on 2012-09-10
Try using the full path for the gsettings command.
You can find out what this is by doing:
```
which gsettings
```

---

### Post by natespaceorama on 2012-09-10
Alas, no. The script still works when I run it manually, but as the minutes tick by, my wallpaper remains unchanging.

---

### Post by Cheesemill on 2012-09-10
I think you may need to tell the cronjob which display you want it to affect.

Be default cronjobs have a very limited number of environmental variables set, it doesn't even know that you have an X server running.

Try editing your crontab to read:
```
* * * * * env DISPLAY=:0 && ./randomwallpaper.sh
```

---

### Post by natespaceorama on 2012-09-10
Huzzah! Thank you. That fixed the problem.

---

