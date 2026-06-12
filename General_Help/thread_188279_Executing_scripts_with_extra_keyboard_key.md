---
title: "Executing scripts with extra keyboard key"
date: 2006-06-03
forum: General Help
---

### Post by chiron80 on 2006-06-03
I recently upgraded to Ubuntu 6.06, and apparently during the upgrade tpb (Thinkpad Button) was uninstalled because it conflicts with hotkey-setup. tpb allowed me to configure what happened when I pressed the extra buttons on my Thinkpad keyboard, in particular the "ThinkVantage" button.

I've gotten all the keys working (that I've tried, all the F- keys) except the "ThinkVantage" button. With tpb I could modify one line in /etc/tpbrc to reprogram that happened when that button was pressed. Now I can't seem to find how to configure what happens when I press that button.

Using xev I determined that the button is assigned keycode 159. If I wanted to make that button mirror another button I could use xmodmap, but what I want is to get a script to run (I haven't decided what script yet, but that comes next).

Does anyone know how to excecute a script when a button is pressed on the keyboard?

- Ben

---

### Post by carlos1 on 2006-06-04
There may be a better way, but the one way I know (at least in KDE) is to add the script to the menu, maybe add a menu category called "scripts", then put the command information in with the menu editor. 

Then Go to SYstem Settings->Regional&Accesibility, click "keyboard shortcuts" Select the "command shortcuts" tab, then find your script on the menu (it will be in the same sequence at the KDE menu), click the "custom" radio button on the bottom, and then when the box pops up, press the key you want as a shortcut. 

There is probably a better way to do this form the command line but htis way works for me.

---

### Post by chiron80 on 2006-06-05
[QUOTE=carlos1]There may be a better way, but the one way I know (at least in KDE) is to add the script to the menu, maybe add a menu category called "scripts", then put the command information in with the menu editor.[/QUOTE]
Thanks for the information about KDE. Unfortunately, at the moment I'm using Gnome, although I've considered switching to another Window Manager (not necessarily KDE), but I was hoping for an option that didn't rely on any particular Window Manager.

I've looked for Gnome specific options as well, and haven't found one... the "Keyboard Shortcuts" option under "System" -> "Preferences" appears to have only a limited selection of operations that can be performed.

---

### Post by computx on 2006-07-15
For many default actions in gnome this is pretty easy to do. Go to System - Preferences - Keyboard - Shortcuts.
Find the action you want the button to do, click on the shortcut area then press the Thinkpad key. You are done. I have my thinkpad set to open my home folder this way.

---

### Post by chiron80 on 2006-07-15
> **computx said:**
> For many default actions in gnome this is pretty easy to do. Go to System - Preferences - Keyboard - Shortcuts.
Find the action you want the button to do, click on the shortcut area then press the Thinkpad key. You are done. I have my thinkpad set to open my home folder this way.

I just found what I was looking for, the ability to define custom commands in gnome. It isn't independent of window manager, but it will do for now.

> If you want to add keyboard shortcuts for other commands, you press Alt-F2 and type gconf-editor to open the Configuration Editor, then navigate to Apps > Metacity. Within Metacity, you define the command in Keybinding Commands and define the keyboard shortcut in Global Keybindings.
The advantage to the Configuration Editor approach is that you can define a keyboard shortcut for just about any command you can think of. The disadvantage is that you have to type out the keyboard shortcut. You can't just press Control-Shift-A. You have to type <Control><Shift>a
(Copied from [http://bdmorrison.com/ubuntu/kdegnome.html]("http://bdmorrison.com/ubuntu/kdegnome.html"))

---

### Post by Lunar_Lamp on 2006-07-15
I think xbindkeys is what you are looking for.

---

