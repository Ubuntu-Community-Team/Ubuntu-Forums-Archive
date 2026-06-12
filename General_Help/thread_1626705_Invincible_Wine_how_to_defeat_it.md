---
title: "Invincible Wine how to defeat it?"
date: 2010-11-20
forum: General Help
---

### Post by a quarter past seven on 2010-11-20
hi, im trying to get rid of wine and a program ive installed on wine it, but it just keeps coming back,

ive tried uninstalling it in software sources and in synaptic package manager and ive deleted the .wine folder and all files associated with the program im trying to get rid of except its .iso's which i put in a new folder and ive deleted all the drives i made in winecfg that i needed to run my program and ive tried sudo apt-get wine purge1.3 but its still the 4 wine folders are still there in menu editor and can still partially run the program im trying to get rid of and when i restart its back to the begginning

any ideas on what im doing wrong?


(im on ubuntu 10.10)

---

### Post by a quarter past seven on 2010-11-20
if any ones interested its solved i deleted all the wine packets i could find in synaptic and removed all wine programs  in software sources then i typed locate wine in the terminal and then individually deleted most of the files shown and now its gone at last,

---

### Post by Hippytaff on 2010-11-20
have you tried purge?

if you don't know wtf I'm on about post back :-)

---

### Post by a quarter past seven on 2010-11-20
yep i tryed purge but it just kept installing earlier versions of wine in its place, but its all reinstalled now though and working fine so its all good,

i was doing sudo/apt thing and then id put purge wine1.3 then the 1.2 and so on but it kept coming back,

is their any other purge commands or delete commands for the terminal

and is purge just for uninstalling specific programs? or can you use it with like a key word so that you could type purge example and it would remove all files called example and any files associated with it

thanks for the help,

---

### Post by WorMzy on 2010-11-20
Wine program associates persist because they create .desktop files in ~/.local/share/applications

Delete all the wine-*.desktop files from there and they should disappear from your "Open with" menus, and stop being associated with certain file types.

If you have been using wine correctly, then deleting .wine *will* remove all traces of the actual applications, and there is no way that they can remain partially installed.

If you've used sudo with wine (read: used wine incorrectly), then it may have installed the applications to /root/.wine, in which case, remove that folder with

```
sudo rm -r /root/.wine
```

---

### Post by 3Miro on 2010-11-20
Wine has system files that you can uninstall with purge and .wine folder in your home folder. Wine also installs stuff in other folders if you wall wine with:
```
 WINEPREFIX="/some/folder" wine some_windows_program.exe 
```

Menu entries can be disabled with right-click on the menu, or deleted from  either of:
```

/usr/share/applications
/home/your_user_name/.local/share/applications

```

File associations can be fixed by right-click on a file and then select Properties (open with or something like that). If done once, it will be valid for all files of that type.

---

