---
title: "Keyboard shortcuts in gnome"
date: 2006-04-22
forum: General Help
---

### Post by Antimatter3009 on 2006-04-22
Hey is there any way to set up custom shortcuts in Ubuntu Dapper/gnome? I know about the config gui, but that only has a list of predefined shortcuts that you can set keys for. While that covers most things I want to see, there are a few other programs I would like to bind to a hotkey. In KDE you had the option to bind any program to any key combination. Is there something similar in gnome? Thanks.

---

### Post by aysiu on 2006-04-22
Go to Applications > System Tools > Configuration Editor > Apps > Metacity

You'll see two menu entries there:

Global keybindings
Keybinding commands

In Global keybindings, define the keyboard shortcuts you want
In Keybinding commands, define the command you want executed

---

### Post by passonno on 2006-06-05
Forgive me, but I cannot figure out the gconf editor.

Here is what I want to do:

I want to assign a shortcut to 3ddesk.

Any help?

---

### Post by aysiu on 2006-06-05
In Keybinding Commands, pick an empty command--let's say it's Command_1.

Double-click the empty space next to it and type ```
3ddesk
```

Then, in Globaly Keybindings, pick the same command, Command_1 and double-click on the empty space there, and type your keyboard shortcut. You can't just press Control-Shift-3, for example. You have to actually type the words ```
<Control><Shift>3
```

---

### Post by mmendez on 2007-10-13
Hi this post would seem to be the answer to my question. I have an Acer Ferrari 4000 on the top right it has 4 special keys. One of them the "mail" key opens Evolution, in the Keyboard Shortcuts the key is 0xec. I wanted to open up firefox and go to gmail so I tried putting that key in the gconf-editor>apps>metacity>global_keybindings as both 0xec or <0xec> but neither gives me anything. The command that I put is ```
firefox mail.google.com
```

Thanks
Manny

---

