---
title: "can't do anything after update"
date: 2009-09-25
forum: General Help
---

### Post by epidemiks on 2009-09-25
i just did an update which required a reboot, after which I can't do anything!
i can log in, and gnome comes up, but i'm unable to click on anything.. mouse moves around, wifi connects, then nothing. can't click on menus, awn, logout.. keyboard is unresponsive, ctrl alt backspace does nothing. i have to hard power down.. what on earth has happened?:confused:

---

### Post by Diabolis on 2009-09-26
When I get that I press **<Ctrl><Alt>F1**, log in and execute:
```
top
```

To see if a process is consuming all the CPU, if thats the case I kill it:
```
killall "process name"
```

Of course this is not very recommended if you haven't saved any important files or the stability of the system depends on that process.

---

### Post by epidemiks on 2009-09-27
> **Diabolis said:**
> When I get that I press **<Ctrl><Alt>F1**, log in and execute:
```
top
```

To see if a process is consuming all the CPU, if thats the case I kill it:
```
killall "process name"
```

Of course this is not very recommended if you haven't saved any important files or the stability of the system depends on that process.

Cheers for that, handy to know.

Turns out it fixed itself anyway after i left it off overnight.

---

