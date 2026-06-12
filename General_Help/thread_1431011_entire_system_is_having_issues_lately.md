---
title: "entire system is having issues lately"
date: 2010-03-16
forum: General Help
---

### Post by eival on 2010-03-16
8.04 has been really slow its almost to the effect of when windows has a virus, things start happening that theres no answers for.

some of my apps dont even work like GTK Record my Desktop, it just hangs, even GIMP has started to messup, ive had things where the work space whites out completely an i have to kill it.


anyone else experiencing this?

is this just a hidden attempt to force us to upgrade?

---

### Post by prodigy_ on 2010-03-16
> **eival said:**
> things start happening that theres no answers for.
Are you sure that your HDD is ok? I'd check its SMART data first.

---

### Post by eival on 2010-03-16
i just tried to uninstall 2 wierd apps and now my entire applications tab doesnt evne appear, places and system appear fine, this is nothing to do with the HDD.

and now i tried removing it from the toolbar an putting it back an its not on the far left, i cant move it and the firefox is now all the way on the left.

why cant i move these?

---

### Post by eival on 2010-03-16
okay i pinpointed the issue, theres some wierd program that installed thru wine its located under Applications > Other

if i try to remove them from the menu using menu editor it deletes the application menu file from home/username/.config/menus/application.menu

i already figured out how to fix that.

but now i need to figure out how to remove these bad apps from my system.

i already removed wine and deleted its folder but those 2 apps are still on my system, the description/name is some scrambled weird characters so im assuming its some type of windows trojan.

any thoughts?

is there a sudo command that will wipe out everything ever installed thru Wine?

i cant even search for these apps in synaptic cause like i said the names of them are scrambled characters and icons.

---

### Post by ushills on 2010-03-16
All the wine application are stored in your .wine folder, I would suggest the following

```
sudo apt-get remove --purge wine
sudo rm -r ~/.wine
sudo apt-get install wine
```

---

### Post by 3rdalbum on 2010-03-16
If certain programs are messing up, you should try deleting their preferences files. They are stored in hidden folders in your home directory. Press Control-H in your home directory to see them.

---

### Post by eival on 2010-03-16
[IMG]http://i42.tinypic.com/2hqdmqw.png[/IMG]


theres a screencap of the 2 wierd programs.

if i try to delete them from that menu it deletes my application file like i said above.

and i assume its either some language that isnt installed on the Ubuntu so those weird characters are shown instead.

since i purged the .wine directory i dont have that folder, any thoughts where these files/apps would be on my file system?


edit- i also reinstalled wine to see if they would appear in the folder but they still didnt.

i also tried running the apps to see the name in the system monitor but only wine appears in the list but the app never starts an just ends itself a few seconds later.

---

### Post by prodigy_ on 2010-03-16
Can you right-click and add these launchers to desktop? Then you'll be able to see their properties and check "Command" field. After that just browse your /usr/share/applications folder. All launchers should be there.

For example, Main Menu editor is launched with "alacarte" command. Its launcher is /usr/share/applications/alacarte.desktop.

---

### Post by eival on 2010-03-16
okay that let me see the directory, which was in the WINE C directory but since i removed that, the folder its listed under isnt there, so i guess i need to just delete these from the list but doing it thru menu edit is screwy.

i looked in the applications.menu file located (etc/xdg/menus/) but it doesnt list the individual apps. it just lists the catagories(graphics/internet/office)

is there an actual config file that has the actual list of apps that would allow me to simply delete those 2 apps from the list an save/update the list, under sudo?

---

### Post by J V on 2010-03-16
A windows virus affecting linux through wine? Well thats a new one :P

Before you delete them, please run clamtk so we can find out what these nasty things are (also, how did they get on your computer?)

---

