---
title: "Close terminal, kill the app that's running"
date: 2010-05-15
forum: General Help
---

### Post by Scooter_X on 2010-05-15
So, this may have something to do specifically with conky, but I don't understand how sometimes when I run 'conky' from the terminal and then once it loads I close the terminal, it kills conky. But other times, I do the same thing, wait for it to load, and it just keeps running! In both cases, I don't get a "user@computer~:$" prompt back after running 'conky' either. That happens sometimes with other things like gedit too... anyone know why? Running Karmic if that helps.

---

### Post by kerry_s on 2010-05-15
it's suppose to close unless you disown the child process.
you should be using alt+f2 to launch programs.

---

### Post by vkcaspervk on 2010-05-16
Conky has a variable that you can add to the config that will always force it to run in the background. 

```
# set to yes if you want Conky to be forked in the background
background yes
```

To fork something into the background add a & to the end of the command. Doing this will give you the PID and you can close the Term. 
```
me@me-desktop:~$ scite &
[1] 27368
me@me-desktop:~$
```

---

### Post by Scooter_X on 2010-05-16
Thanks a bunch you guys. I never knew about either of those solutions, and they both help quite a bit. I really appreciate it.

---

