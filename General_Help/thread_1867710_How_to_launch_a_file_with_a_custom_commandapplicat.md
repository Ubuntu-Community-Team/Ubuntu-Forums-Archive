---
title: "How to launch a file with a custom command/application"
date: 2011-10-23
forum: General Help
---

### Post by Aeren on 2011-10-23
Since ubuntu 11.10, it now seems impossible to launch a file with a custom command as could be done until now. However, this is an enormous problem for me, since i'm now developping in pharo. I need to launch pharo files with a custom virtual manchine, and although i've been looking all over the internet since yesterday, I haven't managed to find out how to do it...

There's talk about doing it manually with the mimeapps.list file and with adding a .desktop file for the app, but I still haven't managed to find out how to do it. Any help would be greatly appreciated.

---

### Post by hwttdz on 2011-10-23
Right click on file -> properties -> general tab -> open with -> other application -> custom command (I'm not using quite the "standard" setup but hopefully the options are still the same).  If that doesn't get you what you want, I'd make a script in ~/bin or ~/scripts and essentially make it a wrapper for the virtual machine.

---

### Post by crdlb on 2011-10-23
Use the [alacarte]("apt:alacarte") menu editor to create a launcher for the application. Make sure the command ends with a %f if it accepts a file argument or %F if it accepts one or more: ```
foo %F
```

Without doing anything else, it should be available under 'Other Applications'.

---

