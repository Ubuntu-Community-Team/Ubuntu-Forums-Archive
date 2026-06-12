---
title: "View the display of another computer"
date: 2006-04-06
forum: General Help
---

### Post by ^NoX on 2006-04-06
I use VNC to create my own session and log in on a remote computer.
What I want to do now, is to view exactly what I could view if I was near the computer.
I mean that I can leave the computer running at home, go to work and connect the computer, and then continue my work on my computer located at home.
When I try to use display 0 with VNC, it tells me that display 0 is already taken.
Anyone knows how to do it?

---

### Post by mcwtlg on 2006-04-06
[QUOTE=^NoX]I use VNC to create my own session and log in on a remote computer.
What I want to do now, is to view exactly what I could view if I was near the computer.
I mean that I can leave the computer running at home, go to work and connect the computer, and then continue my work on my computer located at home.
When I try to use display 0 with VNC, it tells me that display 0 is already taken.
Anyone knows how to do it?[/QUOTE]

Just from a VNC standpoint, I am suprised this is an issue.  The default setup allows you to remote control the PC.  VCN is what our help desk desk uses to remote machines, both PC and Unix.

---

### Post by chio on 2006-04-06
I think I get what you're on about - I've got the same trouble. It seems that starting vncserver on the box launches a new instance of GNOME which has no relation to what's on your existing screen.

---

