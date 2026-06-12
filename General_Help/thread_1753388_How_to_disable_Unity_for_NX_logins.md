---
title: "How to disable Unity for NX logins?"
date: 2011-05-08
forum: General Help
---

### Post by mwshook on 2011-05-08
I often use freenx server on my Ubuntu machine, and login using the noMachine NX client on MacOS

When I log in from my Mac, I can setup login options. Under "unix" I have the options of GNOME, KDE, XFCM. I have always used GNOME.

Now, after the Natty upgrade, when I login, there is no panel, no launcher, and no title bars on the windows. Basically there's no Unity. It's not surprising since Compiz doesn't run under NX.

I still want to run Unity when I login locally. Does anyone know of some server-side changes I can make, to run "classic gnome" on remote NX connections?

---

### Post by ulukay on 2011-05-25
did you find a solution to that problem?

---

### Post by mwshook on 2011-05-25
Nope

---

### Post by drsar on 2011-06-13
This is only a partial solution but maybe you can run with it, turn it into something useful and report back:

I log in via opening an xterm in a new virtual desktop. (To do this, I ask for Unix/Custom as the Desktop on NoMachine and run xterm as the command). Once logged into the really bland window, I start and background ```
metacity &
``` followed by starting and backgrounding ```
gnome-panel &
```.

This would work quite nicely in 10.04 and it also kinda works in 11.04. 'Kinda' because there is a quirky feature when you press the d key: The window will get minimized. Not sure and no time yet to find out what to do.

Let me know what you find.

---

