---
title: "Make Shut Down, shut down?"
date: 2010-04-12
forum: General Help
---

### Post by asddf on 2010-04-12
Is there a way to make Ubuntu shut down when I press shut down? instead of the "Ubuntu will shut down in 60 seconds"

Thanks!

---

### Post by Klump on 2010-04-12
I think you're looking for this:
```
gnome-session-save --force-logout --gui
```

---

### Post by Doug11 on 2010-04-12
You can try this

[http://ubuntuforums.org/showthread.php?t=1004316&highlight=disable+shutdown+time](http://ubuntuforums.org/showthread.php?t=1004316&highlight=disable+shutdown+time)

---

### Post by codemaniac on 2010-04-12
$ sudo shutdown -h now

---

### Post by Klump on 2010-04-12
Oh, sorry, the command I gave is for logging out, misread your question... :)

---

### Post by sisco311 on 2010-04-12
```
gconftool-2 --type bool --set /apps/indicator-session/suppress_logout_restart_shutdown "false"
```

---

