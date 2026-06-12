---
title: "Running a command for a certain amount of time"
date: 2011-03-25
forum: General Help
---

### Post by supradave on 2011-03-25
Is there a way to run a command for a certain amount of time?  I stream a radio program for 3 hours.  At the end of the 3 hours I currently kill it through cron.  Is there a way to do it without having to have a cronjob kill it?

Through bash, BTW.

---

### Post by vanadium on 2011-03-25
*The* proper way to do this would seem the way you currently do it.

---

### Post by vanadium on 2011-03-25
Maybe a more practical way:
```

(<your program> ; sleep 3h ; <your kill command>) &

```

---

### Post by Cheesehead on 2011-03-25
Depends on the stream command you use. Many have a length-of-time flag.

For example, vlc has --start-time, --stop-time, and --run-time.


Alternately, 'at' might be easier to use than cron for the usage you seem to have in mind.
```

$ at now + 3 hours
warning: commands will be executed using /bin/sh
at> pkill vlc

```

---

### Post by ajgreeny on 2011-03-25
Certainly streamripper, which I use a lot for this purpose, has a -l option for the length of recording/streaming in seconds, eg 
```
/usr/bin/streamripper http://webaddress -t -r -d /home/username/Radio -l 7320
```where the7320 is 2hrs 2min, the extra 2min for safety.

---

