---
title: "install ?"
date: 2005-01-21
forum: General Help
---

### Post by ThePainter on 2005-01-21
Hi,
Im trying to install a downloaded program.
there are two files, a .rpm and a tar.gz
How do I go about installing them ?  :confused: 

Thanks if you can help.

---

### Post by DJ_Max on 2005-01-21
Try to stay away from Red Hat's Package Manager(RPM). The tar.gz is a compressed file in the tarball format. Which is the source.

To install the from the source code, you have to compile it.

or

You can see if there are .deb packages for it.

```
sudo apt-cache search PACKAGENAME
``` 

replace PACKAGENAME with the program you want to install. There are tons of guides around.

---

### Post by ThePainter on 2005-01-22
Hi,
Guess what ?
I found them all there.
Arent the people who make all this possible, nice people ?  =D>

---

### Post by Perfect Storm on 2005-01-22
Nice to see you straight it out.

About the rpms files, you could go 'sudo alien <name>.rpm' and thereafter 'sudo dpkg -i <name>.deb'. I've done that with 3 packages (long live lazyness) and they worked perfect. Though there may be some files which it can't be done, I have read.



.:=The AI Dude=:.

---

### Post by ThePainter on 2005-01-22
Hi,
This looks like it changes the rpm into a deb file ?
What would I do with it after that ?

One more thing, I was looking at your Desktops linked at the bottom of your post they look good, I enjoyed a bit of themeing in XP.
I found how to change the colour and alpha of the top and bottom bars but the task buttons and menu buttons, clock and sys tray all stay that bland gray colour. how do you control the colour of these to be the same as the bar ?

---

### Post by Perfect Storm on 2005-01-22
[QUOTE=ThePainter]Hi,
This looks like it changes the rpm into a deb file ?
What would I do with it after that ?

One more thing, I was looking at your Desktops linked at the bottom of your post they look good, I enjoyed a bit of themeing in XP.
I found how to change the colour and alpha of the top and bottom bars but the task buttons and menu buttons, clock and sys tray all stay that bland gray colour. how do you control the colour of these to be the same as the bar ?[/QUOTE]


Yep, the alien command change package file(s).

cd /where/your/rpm/file/is
sudo alien <name-of-the-package>.rpm

now a .deb file appears in the same folder.
To install it write

sudo dpkg -i <name>.deb

Now it's installed, make sure if the output from the terminal tells you if there are dependency problems, so we can solve it. 


The other question I'm not sure, I'm using themes to change everything.
check: [www.gnome-look.org](www.gnome-look.org) and look for GTK2 themes



.:=The AI Dude=:.

---

### Post by ThePainter on 2005-01-22
Hi,
AI you have been very helpful, thanks.  :D

---

### Post by DJ_Max on 2005-01-22
Wonder why I never came across the 'alien' program. Seems very useful.

If you do alien --help
seems it has more features.

---

### Post by Viro on 2005-01-24
[QUOTE=DJ_Max]Wonder why I never came across the 'alien' program. Seems very useful.

If you do alien --help
seems it has more features.[/QUOTE]
 Alien is very very useful, especially in an RPM dominated world. Thankfully, with more and more distros appearing that don't use RPM, this shouldn't be too much of a problem. It really annoys me when software is distributed only in RPM form.

---

