---
title: "Gnome-Shell Help?"
date: 2010-06-15
forum: General Help
---

### Post by Eximius O Nex on 2010-06-15
[FONT=Verdana][SIZE=2]Hey, I'm new to Ubuntu but I'm pretty computer savvy, I installed Ubuntu fine with out any problems and I found this cool program, I guess it would be called, on the web called Gnome shell. I did as it said to install it threw terminal  
[U][I]$ sudo add-apt-repository ppa:ricotz/testing
$ sudo apt-get update
$ sudo apt-get install gnome-shell[/I][/U]

This didn't work all to well because when I tried to use Gnome-Shell with [/SIZE][/FONT][FONT=Verdana][SIZE=2]"_*gnome-shell --replace*_"
I get this error "_*(mutter:3393): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (/usr/lib/libgjs-gi.so.0: undefined symbol: g_type_info_get_array_type)]*_"
I have absolutly no clue what is going on and any help would be greatly appreciated

Thanks for your time,
Eximius[/SIZE][/FONT]

---

### Post by Eximius O Nex on 2010-06-15
I checked back a few minuetes later and in terminal it said this added to the orginal message "Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1e0002f (Contact Li)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed."

---

### Post by ddrichardson on 2010-06-15
Why are you using a PPA version? Gnome-shell is in 10.04 repository - I would try that first.

---

### Post by Eximius O Nex on 2010-06-15
Uhhhh.... What do you mean by that?

---

### Post by ddrichardson on 2010-06-15
Well you've added a repository, there was no need to as there is a version in 10.04 - the only step needed was sudo apt-get install gnome-shell.

---

### Post by Eximius O Nex on 2010-06-15
Ok, So what should i do now?

---

### Post by ddrichardson on 2010-06-15
Go to System->Administration->Software Sources and under "Other software", untick the PPA from your original post.

Open a terminal and do:
```
sudo apt-get autoremove gnome-shell
```
Then:
```
sudo apt-get install gnome-shell
```

Or install from the software centre if you prefer.

---

### Post by Eximius O Nex on 2010-06-15
ok now i got "(mutter:4960): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x3a00b14 (eximius@ex); these messages lack timestamps and therefore suck." When I do "gnome-shell --replace"

---

### Post by ddrichardson on 2010-06-15
Does gnome-shell run? These are warnings, not errors.

---

### Post by Eximius O Nex on 2010-06-15
Ummm well I sound like an idiot but I don't know how to open it i check the menu under applications and all under systems and I can't find "gnome-shell"

---

### Post by ddrichardson on 2010-06-15
Well, when you type gnome-shell --replace, to get the warning, isn't anything happening? There isn't an entry for it because it replaces a part of the windowing system.

---

### Post by Eximius O Nex on 2010-06-15
I think I got it, When I put "Gnome-Shell" into terminal it responds with this "(mutter:6288): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager."
and when I try doing "Gnome-shell --replace" its responds with "(mutter:6293): mutter-WARNING **: Plugin API mismatch for [/usr/lib/mutter/plugins/libgnome-shell.so]" 
So unfortunatly the same problem :(

---

### Post by Eximius O Nex on 2010-06-15
No nothing happens it all remains the same

---

### Post by ddrichardson on 2010-06-15
This is because of the PPA version - [http://art.ubuntuforums.org/showthread.php?p=9173974](http://art.ubuntuforums.org/showthread.php?p=9173974)

Follow his direction and let us know.

---

### Post by Eximius O Nex on 2010-06-15
SWEET! I got it running but terminal gave me this... 
"(mutter:6925): Clutter-WARNING **: The actor 'BigBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'searchEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'BigBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'dash' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
Window manager warning: Log level 16: IA__g_object_set_valist: construct property "type" for object `ShellEmbeddedWindow' can't be set after construction

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'StBin' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:6925): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended" 


Sorry for the length... and when i go to close terminal it says a process is still running

---

### Post by ddrichardson on 2010-06-15
You're almost always going to have warnings, for the most part these can be ignored.

The program is launched from a terminal so you will have a warning when you close the terminal as it will also close gnome-shell. There's a way around that but it's not really what you want, if you want it loaded at login then add it to the startup by clicking System->Preferences->Startup applications. Add then set the command to gnome-shell --replace and the name to Gnome-shell.

Logout and back in.

---

### Post by Eximius O Nex on 2010-06-15
How do I access system in Gnome-shell?

---

### Post by ddrichardson on 2010-06-15
type gnome-session-properties

---

### Post by Eximius O Nex on 2010-06-15
alright, sweet, thank you very much

---

### Post by Temellin on 2010-06-17
Hey, I had the same issue after going from the basic PPA gnome-shell install to the Ricotz PPA one, I would get similar mutter errors but fixed this by opening Synaptic Package Manager and selecting "Mark All Upgrades" it updated Mutter, Clutter and a few other things (Sorry for the lack of details :/) and then I was able to run it (The newer version, not the outdated one) fine by pressing F2 and typing ```
gnome-shell --replace
```

---

### Post by cjalves on 2010-07-17
thanks temellin that worked for me

---

