---
title: "New upgrade"
date: 2011-11-09
forum: General Help
---

### Post by St Nabi on 2011-11-09
Hi all, 

Just upgraded to 11.10 and it all seemed fine. i then went to compiz manager and made a few tweaks, (enable desktop cube, 3d windows, wobbly windows) and pop !!!

I lost the dash and every icon on the desktop...
I cannot access the dash by even pressing Alt F2. 
I cannot access anything and can't even get the system to make sense of anything I type.

Help ?

---

### Post by Paddy Landau on 2011-11-09
Hmm, tricky.

Try this:


[LIST]
[*]Alt-F2 and *gnome-terminal* to start a terminal.
[*]Enter *unity --reset*.
[*]Log out and in again (if you can't, press Ctrl-Alt-Delete and reboot).
[/LIST]

Does that fix it? If not:


[LIST]
[*]Alt-F2 and *gnome-terminal* to start a terminal.
[*]*sudo apt-get install ccsm* (it may be already installed, in which case don't worry).
[*]*ccsm*
[*]Click *Desktop* (on the left).
[*]If checked, clear the checkbox for Ubuntu Unity Plugin.
[*]Now check the checkbox for Ubuntu Unity Plugin. You may get several conflict warnings; in every case click the right-hand button to resolve it.
[*]Warning: you may have to wait a couple of minutes even on a new computer.
[*]Log out and in again.
[/LIST]

If that still doesn't work:


[LIST]
[*]Alt-F2 and *gnome-terminal* to start a terminal.
[*]*rm ~/.config/dconf/user* (this will lose all your ccsm settings)
[*]Log out and in again.
[/LIST]

---

### Post by St Nabi on 2011-11-09
> **Paddy Landau said:**
> Hmm, tricky.

Try this:


[LIST]
[*]Alt-F2 and *gnome-terminal* to start a terminal.
[*]Enter *unity --reset*.
[*]Log out and in again (if you can't, press Ctrl-Alt-Delete and reboot).
[/LIST]

Does that fix it? If not:


[LIST]
[*]Alt-F2 and *gnome-terminal* to start a terminal.
[*]*sudo apt-get install ccsm* (it may be already installed, in which case don't worry).
[*]*ccsm*
[*]Click *Desktop* (on the left).
[*]If checked, clear the checkbox for Ubuntu Unity Plugin.
[*]Now check the checkbox for Ubuntu Unity Plugin. You may get several conflict warnings; in every case click the right-hand button to resolve it.
[*]Warning: you may have to wait a couple of minutes even on a new computer.
[*]Log out and in again.
[/LIST]

If that still doesn't work:


[LIST]
[*]Alt-F2 and *gnome-terminal* to start a terminal.
[*]*rm ~/.config/dconf/user* (this will lose all your ccsm settings)
[*]Log out and in again.
[/LIST]
Alt F2 does not work...

There is a sort of toolbar at the top which has File, Edit, View, Go and Help as headings but they are of no use.
Like I said, there does not seem to be any recognition.
Would it not be better to do a re-install ?
However, i would like to know what caused this if possible.

Cheers

---

### Post by Paddy Landau on 2011-11-09
> **St Nabi said:**
> Alt F2 does not work...

If you press Ctrl-Alt-T do you get a terminal? If so, you can proceed with the instructions.

Otherwise, as a last resort, press Ctrl-Alt-F1. You will get a black terminal. Log in. Proceed with the instructions in the first part:
```
unity --reset
```
To reboot from there, press Ctrl-Alt-Delete.

If that still doesn't work, go back to Ctrl-Alt-F1 and follow the last instructions:
```
rm ~/.config/dconf/user
```

---

