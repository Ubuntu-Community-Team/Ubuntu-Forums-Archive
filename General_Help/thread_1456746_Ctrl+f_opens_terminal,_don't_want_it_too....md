---
title: "Ctrl+f opens terminal, don't want it too..."
date: 2010-04-17
forum: General Help
---

### Post by wwarsin on 2010-04-17
Hey everyone, i just reinstalled ubuntu today... and after installing all my stuff i'm having a problem, when i press ctrl+f in firefox it opens a terminal, i can't figure out how to stop it from doing this.

I looked in System -> Preferences -> Keyboard Shortcuts but there is nothing listed for ctrl+f, how can i stop this? (it doesn't just happen in firefox, it happens in all programs)


-Thanks

---

### Post by ajgreeny on 2010-04-17
Should be Ctrl+T, as you probably know already, so set that in the keyboard shortcuts, if it's not already there and see if it now stops Ctrl+F doing so.

---

### Post by wwarsin on 2010-04-17
i added it to ctrl+t, and ctrl+f still opens it... i just noticed that it opens like a mini-terminal, there are no "File" "Edit"... buttons, and it opens up smaller then other terminals..

this getting annoying cause firefox won't even see the ctrl+f for search...

---

### Post by drs305 on 2010-04-17
If it happens in all programs you can check the global keysbindings with gconf-editor. Open gconf-editor with the following command. It will take you to the global keybindings section. See if <Control>f is listed anywhere in this section. If so, you can 'unset' it by right clicking on the value and choosing 'Unset'.
 
```
gconf-editor /apps/metacity/global_keybindings/run_command_1
```

The 'keybinding_commands', the section below the one that opens, assigns the command to the key selection. You can remove or change the command from that section.

---

### Post by coldraven on 2010-04-18
In Firefox you just have to press / (forward slash) to search a web-page.
It opens a little search bar in the bottom left corner.
So if I was searching for the word "volcano" I just have to type "/vol" and it would highlight all instances of it on the page. Then press F3 to jump to the next instance.
That's one key press quicker than Ctrl-f :)

---

### Post by wwarsin on 2010-04-18
i looked in the gconf-editor and didn't see <Control>f, i even did a search (including the keys and values) and it didn't find anything either...

i use control+f in other applications too, so the / in firefox is nice, but doesn't solve my problem.

---

### Post by ajgreeny on 2010-04-18
Sounds from your description of the terminal window as if it is xterm that is opening, not gnome-terminal.  Run xterm from the Alt+F2 dialog to check that I'm right, then search in the keyboard shortcuts etc etc for *xterm*, to see if you can find anything.

---

### Post by wwarsin on 2010-04-18
yea, it is xterm, and no i did not find anything in the gconf-editor

edit: i just did sudo apt-get remove xterm, then tried to do a ctrl+f and now it will not open the search feature in firefox, in the edit menu it still shows "Find       Ctrl+F"... :(

---

### Post by wwarsin on 2010-04-18
well thats wierd.... i just restarted because compiz messed up... and what d'ya know? ctrl+f works like it should :/ maybe it was something i installed? but i'm glad it went away....


Kinda off topic but is there an easy way to see a list of installed things? I'm used to windows add/remove apps, but i know with linux theres probably hundreds of things installed, but how can i view/search what i have installed, synaptic doesn't seem to let me do that (easily)

-Thanks

---

### Post by drs305 on 2010-04-18
> **wwarsin said:**
> Kinda off topic but is there an easy way to see a list of installed things? I'm used to windows add/remove apps, but i know with linux theres probably hundreds of things installed, but how can i view/search what i have installed, synaptic doesn't seem to let me do that (easily)

The Ubuntu Software Center (Applications, Ubuntu Software Center) is a friendly GUI app that can show you installed apps.

Old-timers might still recall you can view your installed applications via "aptitude", typed in a terminal. It has things broken down into categories. It probably would be a bit strange to anyone not comfortable or familiar with it, but it's worth taking a look just to see how things in the computing world used to be.  ;-)

---

### Post by ajgreeny on 2010-04-19
You can see you history of installed applications with synaptic and the update manager using **synaptic - file - history**.  It does not show things installed in terminal with either dpkg or apt-get, unfortunately, but there are many logs in **/var/log/dpkg.log** which tell all.

---

### Post by shteren on 2010-10-22
well about your original question, your problem was probebly xbindkeys, it adds Ctrl+f as a key bind to open xterm by default, you can delete this bind.

just type xbindkets-config in terminal and change it.

---

### Post by yashao13 on 2012-01-18
[B]hello,
 
comment all the lines with xterm in :
vi $HOME/.xbindkeysrc

after :
[/B][B]killall -HUP xbindkeys

that's all
+
[/B]

---

