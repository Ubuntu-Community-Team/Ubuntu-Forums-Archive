---
title: "Programs Added to Gnome Menu Don't Want To Run"
date: 2009-08-24
forum: General Help
---

### Post by Yanatsu on 2009-08-24
So, I know how to add a program to the Gnome menu, or at least I think so. But how do I get a program that's in a specific location to run? I'll use a game called AssaultCube as an example-it runs from a shell script, but it's the same with other programs that don't. 
```
./assaultcube.sh
``` works fine from console, and double-clicking it from the file manager works, too, but when I click on the entry I've made in the menu, nothing happens. Is there any specific manner in which I need to put in the command? I'm just using 
```
/home/sean/applications/AssaultCube_v1.0.2/assaultcube.sh
```in the command field. It works fine for Firefox 3.5 like that, but some programs just don't like me. Help?

---

### Post by j7%&lt;RmUg on 2009-08-24
Gnome-menu looks in a specific place for its applications, I cant remember off the top of my head but when i get home from work in just over an hour i will have a look and post back here.

---

### Post by Yanatsu on 2009-08-25
It works with some applications, though. My FF 3.5 is in ~/applications/firefox/
But other programs don't work when I type the path to them...

---

### Post by tgeer43 on 2009-08-25
I believe that with shell scripts you will need to prepend your commans with 'sh' thusly:
```
sh /home/sean/applications/AssaultCube_v1.0.2/assaultcube.sh
```Try that and see if it works.

tgeer

---

### Post by Yanatsu on 2009-09-01
Sorry for the long reply time, I kind of forgot about this.
And I've tried that. It doesn't work, and again, it doesn't work with applications. Not just scripts, but applications. I have no idea why Firefox 3.5 works and others don't, but it does.

---

