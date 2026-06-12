---
title: "Is there a shell command to check if a process is running?"
date: 2011-01-27
forum: General Help
---

### Post by ninjaaron on 2011-01-27
I'm trying to write a script that toggles one of my daemons on and off, so I need a command that checks if the process is running and returns some kind of answer.

---

### Post by Escoba on 2011-01-27
Try

```
ps -u $USER | grep processname
```

---

### Post by ninjaaron on 2011-01-27
Well, that seems to work. The difficulty now is that the process is unclutter, a daemon that starts at login but doesn't appear in my startup applications. I don't know where it's launching from, but I think that is the problem

When I pkill it, it leaves an entry in the list with the a [FONT="Courier New"]<defunct>[/FONT] tag after it. If I start a new instance, the old entry remains. If I kill the new instance, it's entry is deleted, but the initial instance is always there.

I need to find out how to keep it from loading at startup. It starts early in the login process, but it isn't on in the login screen. Where is it hiding?

---

### Post by tgalati4 on 2011-01-27
Most startup processes are listed in /etc/init.d.  There's a README in that directory that explains how the startup scripts work.

---

### Post by ninjaaron on 2011-01-27
I either didn't understand the readme, or it was not very helpful. In any case, none of the scripts had 'unclutter' in the name. I also checked in the "x11-common" script, since I figure the mouse must have something to do with that.

No luck yet.

---

### Post by ninjaaron on 2011-01-27
Found the answer:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1450975](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1450975)
Worked.
All is well.

---

### Post by tgalati4 on 2011-01-27
The other place you can find startup scripts is in /etc/default.  But then you figured that out already.

---

