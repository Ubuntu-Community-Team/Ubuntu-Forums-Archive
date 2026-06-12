---
title: "Separate X Screen Help"
date: 2009-10-15
forum: General Help
---

### Post by Dus10lpatton on 2009-10-15
So at this time im running the twin view option for multiple monitors which is nice but i really want to run the separate x screen display. Every time i try my second display goes out and nothing pops up any help on this issue would be greatly appreciated!

---

### Post by mocoloco on 2009-10-15
When does your second screen go out, is it after logging out and back in?  That would mean the changes aren't being saved.  How are you setting it up, are you using the "Nvidia X Server Setttings" tool or something else, or editing files by hand?

---

### Post by Dus10lpatton on 2009-10-15
> **mocoloco said:**
> When does your second screen go out, is it after logging out and back in?  That would mean the changes aren't being saved.  How are you setting it up, are you using the "Nvidia X Server Setttings" tool or something else, or editing files by hand?

im using the nvidia settings

---

### Post by mocoloco on 2009-10-15
OK, I looked at my settings tool, I forgot using the separate X screen always requires restarting X (aka, log out and back in).  So the way it's install by default is dumb because you need admin (root)rights to change X settings but the nvidia settings tool isn't set up to run that way by default.  So do this, 
[LIST=1]
[*]Right click on your menu bar (on any of the 3 words Applications, Places, or Settings) and hit "Edit Menus"
[*]On the left select "Administration" and on the right select the nvidia tool
[*]Click "properties"
[*]In front of the command put the word "gksu" so it will say "gksu /usr/bin/nvidia-settings"
[*]Hit close, close the menu editor
[/LIST]

That will make the tool run with the right privileges, which means it will ask for your password.  Now after you set up your second screen, click "Save to X configuration file". I think it will ask if you want to merge and choose that.
Then log out and back in and it should now have two separate X screens.

---

### Post by Dus10lpatton on 2009-10-15
i did everything that u said and i get this error"Unable to create new X config backup file '/etc/X11/xorg.conf.backup"

---

### Post by Dus10lpatton on 2009-10-15
ok so i reset the machine and the error message went away also i got the dual display working correctly!

---

### Post by choyak on 2009-11-01
Thanks much for the tip of editing menus and adding 'gksu' to the command.  This is very helpful not just for nVidia but Nautilus and other also so I can unlock arbitrarily locked directories on my net drive

---

