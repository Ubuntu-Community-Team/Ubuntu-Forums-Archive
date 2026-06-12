---
title: "Gnome terminal default size"
date: 2010-09-28
forum: General Help
---

### Post by ojve on 2010-09-28
All of a sudden I can no longer control the default size of my gnome terminal windows. The option is just gone from the preference window. If I look in gconf-editor my old values are still there but they are ignored.

Does anyone know how to solve this?

---

### Post by nothingspecial on 2010-09-28
Don`t know what`s up with the gnome-terminal launcher.

But you could map a keybinding to a command that opens it with a specific geometry

```
gnome-terminal --geometry=50x30+0+0
```

The first number is how many characters wide the terminal is ie how many times you have to press space to get to the end of the line.

The second number is the height ie how many times you press enter untill you get to the bottom

The 2 0s put the top left corner at the top left of the screen, you`ll have to experiment with that.

---

### Post by mcduck on 2010-09-28
I also noticed the option has disappeared.

However I usually just change Gnome's default terminal option to run "gnome-terminal --geometry 120x40"..

The option is in System/Preferences/Preferred Applications, on the System-tab. (note that if you type in "gnome-terminal" it will automatically change to default Gnome-terminal option, so type the geometry part first and then add the "gnome-terminal" to beginning of the command). Also remember to set the Execute flag to "-x".

If you use the launcher in the menu you need to change that command with menu editor as well. The option in Preferred Applications affects terminal windows opened from Nautilus and other programs, while terminals opened from the menu are only affected by the command in the menu launcher itself.

---

### Post by ojve on 2010-09-28
Thx, not the optimal solution, but it works at least. Very strange that the option is gone...

//T

---

### Post by Abe666 on 2010-09-28
> **ojve said:**
> Thx, not the optimal solution, but it works at least. Very strange that the option is gone...

//T

I've found exactly the same problem and it is very very painful!! I don't understand why the option from the terminal preferences has disappeared!!

Thanks for the work around though!!

---

### Post by wookiefoot on 2010-09-30
Add the following line to your .bashrc file (of course you can change the dimensions to whatever you want):
```
alias gnome-terminal='gnome-terminal --geometry=80x42'
```This will make every call of *gnome-terminal* actually call *gnome-terminal --geometry=80x42*. This way you don't have to go around and change the various launchers you have set.

You will probably have to log out & back in for this to take effect.

Edit: this only works if you are launching gnome-terminal via bash, which does **not** include most shortcuts or menu items (or, sadly, gnome-do).

---

### Post by kb2001 on 2011-02-04
I had this same problem, I noticed that the option in termcap/sterm wasn't working.  However, I found that it is much easier than the above solutions.  It seems that this option is now part of your profile.  From the menu bar, select "Edit->Profiles...", and click "Edit" to edit the Default profile.  Default size is now an option in this menu, previously it was not.

I'm using gnome-terminal version 2.29.6 on Ubuntu 10.04.01

---

### Post by ronnieredd on 2011-03-27
Using a new install of 10.04.1 64bit. I do not have a "default size" as stated above.
There are some default sizes one can choose from now under the "terminal" menu option.
Try this:
[CODE]gconftool-2 &#8211;set \
/apps/gnome-terminal/profiles/Default/default_size_columns \
&#8211;type integer 140

That will give a wider terminal. If I remember correctly, you'll need to re-login (restart gdm) (ctrl-backspace).

---

### Post by pauln600 on 2011-10-20
The disappearance of the xterm configuration options is pretty inexplicable - downright shocking, actually.  Am I missing something?  I hope so.  Right now I'm sitting in front of gnome thinking I might as well be in Windows...

Paul

---

### Post by philinux on 2011-10-20
> **pauln600 said:**
> The disappearance of the xterm configuration options is pretty inexplicable - downright shocking, actually.  Am I missing something?  I hope so.  Right now I'm sitting in front of gnome thinking I might as well be in Windows...

Paul

11.10 has the option now under edit settings. Well it does for gnome terminal I'm not at my pc right now.

---

### Post by pauln600 on 2011-10-20
> **philinux said:**
> 11.10 has the option now under edit settings. Well it does for gnome terminal I'm not at my pc right now.

Many thanks for the reply.  I guess I should be using gnome terminal instead of xterm - not obvious, since there doesn't seem to be a gnome terminal launcher anywhere in sight. 

Paul

---

### Post by mcduck on 2011-10-20
> **pauln600 said:**
> Many thanks for the reply.  I guess I should be using gnome terminal instead of xterm - not obvious, since there doesn't seem to be a gnome terminal launcher anywhere in sight. 

Paul

The launcher is simply called "Terminal". Most Gnome applications use simple descriptive names in their launchers instead of the full program name. ("Text Editor" instead of "Gedit", "Calculator" instead of "Gcalctool", "Passwords and Encryption Keys" instead of "Seahorse" and so on...)

---

