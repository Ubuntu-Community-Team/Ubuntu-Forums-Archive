---
title: "bash scripting, run commands at same time"
date: 2009-09-21
forum: General Help
---

### Post by meg23 on 2009-09-21
I wrote a bash script to record different audio streams, however it waits for the first one to record before moving on to the next stream. Is there something I can add to have all the recordings run at the same time from the script?

---

### Post by DaithiF on 2009-09-21
add a '&' to the end of the command to have it run in the background and allow execution to continue to the next statement in the script.
```
somecommand &
```

---

### Post by kevdog on 2009-09-21
I don't remember the key combination however to bring them out of the background back to the foreground?  Does anyone here know that?

---

### Post by NoaHall on 2009-09-21
bg and fg

---

### Post by Copernicus1234 on 2009-09-21
And 'jobs' to list the processes you put in the background.

---

### Post by sisco311 on 2009-09-21
```

command        # Ctrl+z to stop it
bg "%command"  # start it in background
fg "%command"  # resume in foreground

```

```
man bash # search for fg and bg
```

---

