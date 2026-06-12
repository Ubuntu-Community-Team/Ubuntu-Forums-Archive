---
title: "Conky Quirk"
date: 2011-06-26
forum: General Help
---

### Post by brodeur235 on 2011-06-26
I have conky installed and set up as a startup application, however everytime I log out and back in conky creates itself as a new window:

[this]("http://i.imgur.com/Z20VQ.jpg")

Which I fix everytime with:

killall conky
conky

to get:
[this]("http://i.imgur.com/NvV6c.jpg")

How can I get conky to start normally without having to do a manual restart everytime I login?

Help appreciated,

Brodeur235

---

### Post by owenll on 2011-06-26
You could try this:

[http://askubuntu.com/questions/37519/removing-conky-drop-shadow](http://askubuntu.com/questions/37519/removing-conky-drop-shadow)

or this

[http://saraithegeek.wordpress.com/2009/04/15/how-to-fix-conky-flickering-borders-and-drop-shadows/](http://saraithegeek.wordpress.com/2009/04/15/how-to-fix-conky-flickering-borders-and-drop-shadows/)

or this

[http://ubuntuforums.org/archive/index.php/t-1112239.html](http://ubuntuforums.org/archive/index.php/t-1112239.html)

---

### Post by TeoBigusGeekus on 2011-06-26
The conky's startup script should have a sleep command.
So, instead of putting
```
conky
```
as a startup app, create a new file, name it conky_start or whatever, add theses lines in it
```
sleep 5
conky
```
make it executable
```
chmod +x conky_start
```
and add this command at the startup apps
```
/path/conky_start
```
Replace path with the appropriate value.
It is an old conky bug that unfortunately hasn't yet been addressed.

---

### Post by brodeur235 on 2011-06-26
Thank you!

---

