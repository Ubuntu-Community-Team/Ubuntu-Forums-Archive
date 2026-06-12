---
title: "Strange file permission issue."
date: 2006-02-13
forum: General Help
---

### Post by equal on 2006-02-13
I don't know why no one answers questions in the Kubuntu section, at least never mine. Does anyone know why I when I right-click a file and change the permissions, I get an error saying "Error KDesktop: /path/to/file.name"

It's really annoying, because I'm trying to rip cds to my mp3 player, but it can't even SEE the files until I can change the permissions, and doing a sudo chmod +777 on each file seems a little complicated for a task that is so easy in gnome.

---

### Post by aysiu on 2006-02-13
[QUOTE=equal]I don't know why no one answers questions in the Kubuntu section, at least never mine. Does anyone know why I when I right-click a file and change the permissions, I get an error saying "Error KDesktop: /path/to/file.name"[/quote] Maybe because [no one's gotten that error before](http://www.google.com/search?hl=en&q=Error+KDesktop%3A+%2Fpath%2Fto%2Ffile.name&btnG=Google+Search)...

> 
It's really annoying, because I'm trying to rip cds to my mp3 player, but it can't even SEE the files until I can change the permissions, and doing a sudo chmod +777 on each file seems a little complicated for a task that is so easy in gnome. Why don't you just do a *chmod* on the whole folder where the files are? ```
sudo chmod -R 777 /equal/music
```

---

### Post by nanotube on 2006-02-13
dont know the fix for your specific problem... but why not do a "sudo chmod 777 *" in the directory of your choice, to change all the files' permissions at once, instead of doing it "on each file" as you say?

---

### Post by equal on 2006-02-13
Either way, in Gnome you can select all the files and do it, but in KDE, no matter what, you get that same error, for example: "Error KDesktop: /home/phil/Music/Big Wig/2006 Reclamation/03 Cross and Burn.ogg"

The chmod -R command is something I was looking for though, thanks that'll help a bit.

---

