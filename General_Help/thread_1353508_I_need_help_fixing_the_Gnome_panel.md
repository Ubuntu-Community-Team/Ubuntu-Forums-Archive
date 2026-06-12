---
title: "I need help fixing the Gnome panel"
date: 2009-12-12
forum: General Help
---

### Post by 37fleetwood on 2009-12-12
well I was playing with 9.10 and installed LXDE which I like to play with sometimes and after I did the Gnome Panel opens Pcmanfm instead of Nautilus. how do I get it back to the way it is supposed to be? I uninstalled and reinstalled the "Menu Bar" andkilled and restarted the Gnome Panel neither of which fixed it. the drive icons on the desktop still open in Nautilus, it's just the panel. I'm hoping it's something simple.
thanks!

---

### Post by zvacet on 2009-12-13
Synaptic>file tab>history and see packages witch you installed to get LXDE and unistall them.You should get gnome back.If you still have troubles to get gnome you can get it to teh defaults with this commands

```
sudo /etc/init.d/gdm stop
```

This command will stop gdm and you will be in terminal so type

```
cd /
cd home
```

If you have more then one account pick one you want to correct.To do that you can look in your home to see all accounts by typing **ls** and go inside of desired account with command 

```
cd username
```


username= your account name

 
After that type

```
rm -rf .gconf* .gnome* .nautilus*

sudo reboot
```

---

### Post by Wardje on 2009-12-13
Uninstalling it completely sounds a bit too radical :P


Try this (I copied this from my post [here]("http://ubuntuforums.org/showthread.php?t=1352582") because I am lazy):
I believe this needed an edit of ~/.local/share/applications/mimeapps.list

So boot up a terminal and type
```
cd ~/.local/share/applications
vim mimeapps.list
```
*Note: you can of course use another text editor than vim. eg: nano, gedit, ...*

Look for a line that says
```
inode/directory=STUFFHERE;
```
Most likely, the STUFFHERE part will start with something like "pcmanfm.desktop" (or something similar, dont know the exact name). Remove the pcmanfm entry (entries are seperated by ;, be sure to remove everything of the pcmanfm entry). Either way, what you want is the nautilus entry to be the first (if there is no nautilus entry whatsoever, put "nautilus-folder-handler.desktop;" right after the "=". Then save.


If this is a systemwide problem, you might have to edit this file instead
```
/etc/gnome/defaults.list
```

---

### Post by 37fleetwood on 2009-12-13
I'm not very experienced and you guys are scaring me. everything is working fine and I would like to keep LXDE the problem is the associations in the Gnome panel that tell it which file manager to start when I click on the "Places" buttom in the upper task bar. how can I simply change the associations back to Nautilus?
please if you are going to give me code please let me know what each step is going to do so I know what to expect and have a better idea if it will fix what I want fixed.

thanks for the help so far;)

---

### Post by Wardje on 2009-12-13
> **37fleetwood said:**
> I'm not very experienced and you guys are scaring me. everything is working fine and I would like to keep LXDE the problem is the associations in the Gnome panel that tell it which file manager to start when I click on the "Places" buttom in the upper task bar. how can I simply change the associations back to Nautilus?
please if you are going to give me code please let me know what each step is going to do so I know what to expect and have a better idea if it will fix what I want fixed.

thanks for the help so far;)


The file ~/.local/share/applications/mimeapps.list associates file types with programs.
If the terminal scares you, you can always open Nautilus, press CTRL+H to show hidden files and folders. Go to your home folder, then open the folder .local, then the folder share, then the folder applications, then double click mimeapps.list to open it in gEdit.
OR you boot a terminal and type (I'll use gedit instead of vim now):
```
gedit ~/.local/share/applications/mimeapps.list
```
which will also open that file.


Then you go to the line that associates programs with inode/directory. This is the line that says
```
inode/directory=STUFFHERE;
```
Instead of nautilus being the first entry, pcmanfm will be there. Remove the pcmanfm entry (entries are seperated by ; ) to make nautilus the first (or move nautilus to the front, whatever floats your boat).
After you changed it, save.

---

### Post by 37fleetwood on 2009-12-13
thanks for being patient here is what that file says:
```
[Added Associations]
application/x-7z-compressed=file-roller.desktop;peazip.desktop;
audio/mpeg=audacious2.desktop;
x-content/image-dcf=f-spot-import.desktop;
video/mp4=totem.desktop;
```

---

### Post by 37fleetwood on 2009-12-13
what would happen if I simply removed pcmanfm? could I simply use Thunar or Nautilus in LXDE?

---

### Post by Wardje on 2009-12-13
That would work too I guess, but before that, try adding this line to that file:

```
inode/directory=nautilus-folder-handler.desktop;
```

and see if it solves things (you might have to restart X for it to take effect)


If *that* doesn't work, then try the same as in my last post but now with a different file. To open it, press ALT+F2 and enter
```
gksudo gedit /etc/gnome/defaults.list
```

If that doesnt have a line that associates inode/directory with pcmanfm, then I'm out of ideas on solving your problem (meaning: fallback to your uninstall plan)

---

### Post by 37fleetwood on 2009-12-13
I added the first line you recomended and it worked perfectly!
thanks so much!!:D

---

