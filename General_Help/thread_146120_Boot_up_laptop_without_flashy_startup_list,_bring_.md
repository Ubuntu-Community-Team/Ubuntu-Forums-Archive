---
title: "Boot up laptop without flashy startup list, bring up terminal and not gdm?"
date: 2006-03-17
forum: General Help
---

### Post by Abdi110 on 2006-03-17
Hi. I've got this 7 year old ThinkPad that I love, I'm also sort of new to Linux. I've installed Breezy on it, most of the stuff I want to do can be done through the terminal. To save on memory, is there any way I can disable the flashy looking start up list thing? The one with the Ubuntu logo and text all in brown on a black background?

Also is there a way to just be dropped into a terminal and not gdm? And if so what command do I need to run to bring up gdm?

Thanks.

---

### Post by Zelut on 2006-03-17
If possible you could re-install the machine & type 'server' at the initial install prompt.  This will not install any of the gdm/gui, etc.  This is a strict terminal-only install.  I've got that on a super old thinkpad as well.  Sure does help on resources.

---

### Post by Abdi110 on 2006-03-17
I'd still like to keep gnome and stuff, just in case I do need a gui.

---

### Post by Zelut on 2006-03-17
what I did in that situation was install 'server', and then add 'ubuntu-desktop'.  This will add all of the gnome desktop packages but if you dont install the gdm then it wont load on boot.

I prefer Xfce for older machines.  I add 'xubuntu-desktop'.(more lightweight than gnome).  If you want to start the gui with this method you can just 'startx'.

---

### Post by gecko on 2006-04-09
[LEFT]The correct command to disable the GUI is[/LEFT]
>  
sudo update-rc.d -f gdm remove

which will remove the startup links to gdm.

---

