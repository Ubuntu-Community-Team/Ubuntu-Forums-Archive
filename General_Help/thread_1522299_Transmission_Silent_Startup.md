---
title: "Transmission Silent Startup"
date: 2010-07-02
forum: General Help
---

### Post by papajonesy on 2010-07-02
Hey guys, quick question. I'm back to Ubuntu after a few months and forgot the switch to make transmission start silently at startup. I looked for the article that helped me last time but to no avail. Thanks :D

---

### Post by warfacegod on 2010-07-02
I'm almost positive that Transmission has that option somewhere in its Preferences. Just look around in there. You may also need to create a Transmission entry in System> Prefs.> Startup Applications. I'm pretty sure the command would simply be transmission

---

### Post by kerry_s on 2010-07-02
> **papajonesy said:**
> Hey guys, quick question. I'm back to Ubuntu after a few months and forgot the switch to make transmission start silently at startup. I looked for the article that helped me last time but to no avail. Thanks :D

```
transmission -m
```

---

### Post by papajonesy on 2010-07-02
No sir, it does not. Kind of stupid seeing as it is the default torrent client for Ubuntu, but oh well. I remember it took me forever to find the command line argument to put in startup. The command was transmission -(the letter I can't remember for the life of me)

---

### Post by papajonesy on 2010-07-02
Thank you so much Kerry! I greatly appreciate it. Bookmarking this for future reference.

---

### Post by orewacrazy on 2012-10-02
> **kerry_s said:**
> ```
transmission -m
```
I got transmission: command not found when i try it on terminal then i try adding -gtk after, become:
```
$ transmission-gtk -m
```
it's work ;)

---

