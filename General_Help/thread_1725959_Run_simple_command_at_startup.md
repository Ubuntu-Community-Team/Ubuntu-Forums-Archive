---
title: "Run simple command at startup?"
date: 2011-04-10
forum: General Help
---

### Post by mYrN on 2011-04-10
Hi.

How would i make ubuntu just execute this 
```
deluged -p 10002 -c ~/delugebig/
```

at startup? Just print it as if i myself would print it in the termial.

Thanks in advance!

---

### Post by ~Plue on 2011-04-10
add the exact command to system > preferences > startup applications?

---

### Post by mYrN on 2011-04-10
It does not seem to work.. Does it run them as root? I think that is needed for this to work.

---

### Post by bodhi.zazen on 2011-04-10
Use the full path to the command and home

So /home/your_user/.config not ~/.config

Also, if you need to to run at boot either write an upstart script or add it to /etc/rc.local

Does it need X to run ?

If you need it to run at login, add it to autostart.

---

### Post by mYrN on 2011-04-10
It needs to start at boot. How do i make this happen?

---

### Post by bodhi.zazen on 2011-04-10
> **mYrN said:**
> It needs to start at boot. How do i make this happen?

Add it to /etc/rc.local using the full path to both the command and configuration file, no shortcuts.

/bin/command not command
/home/your_user not ~

Sometimes rc.local runs too soon, add a sleep before the command if needed.

---

