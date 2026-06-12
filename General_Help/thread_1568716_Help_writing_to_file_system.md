---
title: "Help writing to file system"
date: 2010-09-05
forum: General Help
---

### Post by nexussix on 2010-09-05
Hi all - I'm very new to ubuntu and linux (just installed yesterday)
I've been trying to change the background of the login screen as detailed here

[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

I tried to cut and a paste a photo to the backgrounds folder, which didn't work (the paste option is greyed out), and I tried to save directly to the folder and got the error "cant be saved because you cannot change the contents of that folder. "

How do I unlock the file system so I can write/create folders there?

Thanks

---

### Post by Nythain on 2010-09-05
Whats the folder and what are you using for a file browser/manager?
Very simply you could...
```

gksu nautilus

```
Either from a terminal or from alt+f2.
That will get you pretty much read/write/execute access to almost everything...

[SIZE=3]_**BUT, be warned, while you have this nautilus session open, you will have "root" access to everything, so do NOT go playing around in unfamiliar places with unfamiliar files... regular users are denied access to most of the filesystem for a reason.**_[/SIZE]

---

