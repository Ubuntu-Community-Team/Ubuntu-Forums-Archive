---
title: "How to bind the windows key to run a command (by itself)"
date: 2010-06-28
forum: General Help
---

### Post by ZoraQ on 2010-06-28
So I just upgraded to ubuntu 10.04 and I noticed that my favorite keybinding no longer works as it used to. On previous versions of ubuntu and on other distros, I was able to bind the left windows button to open a terminal _directly_ (i.e. not act as a modifier key for combos like "win + r"). Unfortunately, they changed the behavior of the key so that it has to be a modifier, and the old methods I used to circumvent this no longer work (I would go into gconf-editor and set the "run-command-terminal" option to be run with "Super_L"). Can anyone help me find a way to revert to the old behavior? Thanks.

--ZoraQ

---

### Post by ZoraQ on 2010-06-29
Well, I figured out how to accomplish this in case anyone wants to know. It used to be that I could just go directly into gconf-editor apps-->metacity-->global_keybindings and change the value of "run_command_terminal" to "Super_L", but that doesn't work anymore for whatever reason. So, I figured out that if you go to the system menu-->Preferences--> keyboard --> layout tab and then click the options button, a window will pop up. You then click the "Alt/Win key behavior" section and select the "Hyper is mapped to Win keys" option. After doing this, go into gconf-editor-->apps-->metacity-->global_keybindings--> "run_command_terminal" and change the value to "Hyper_L". It will then work as before. I have no idea why you have to change it from Super_L to Hyper_L, but it works. I hope this helps anyone who likes to bind the terminal to the win key like I do.

--ZoraQ

---

### Post by NT4usB on 2010-06-30
Thanks for posting this.
I fumbled around and mapped the winkey to gnome-terminal way back in Hardy days... haven't been able to duplicate it since. (note to self: take better notes)

---

### Post by Seanlol on 2010-06-30
Thanks for this. I've been trying to find a way to make that key useful.

---

