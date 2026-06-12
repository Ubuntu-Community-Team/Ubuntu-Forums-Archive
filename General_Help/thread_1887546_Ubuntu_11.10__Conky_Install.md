---
title: "Ubuntu 11.10  Conky Install"
date: 2011-11-27
forum: General Help
---

### Post by CrimsonTurkey on 2011-11-27
Okay guys im pretty new to install software in ubuntu and am currently trying to install the conky widget for my desktop im using the Unity Gui and im pretty sure i have installed conky as i can get the version by typing this:
```

chris@BlueTouch:~$ conkyBanshee --version --datatype=TI
conkyBanshee v.2.10

```I'm just wondering how to run it. 

Thanks, Chris

---

### Post by Lebuin on 2011-11-27
If conky is indeed installed, it should just start up when you run in the terminal:
```
$ conky
```Alternatively, you could press ALT+F2, type "conky" (without quotation marks) and press enter.

---

### Post by stinkeye on 2011-11-27
conkyBanshee, is a script to get currently playing info from banhsee.
It is not a widget.
The info is displayed on your desktop with **conky** which you have to install
and create a config which uses the conkyBanshee script.

There is an example config included in the conkyBanshee install which you can copy to your home folder.
In the terminal run...
```
cp /usr/share/conkybanshee/example/conkyrc ~/.conkyrc
```
This will copy the example config and save it in your home folder as **.conkyrc**
The preceding dot makes it a hidden file, (in the file browser ctrl+h to show hidden)

It is saved as .conkyrc because this is the config file that conky looks for when run.

Now when you open a terminal and run 
```
conky
``` 
you should see as shown in pic.I uninstall banshee so it shows "unknown".
It says **@ Rhythmbox** but that appears to be a mistake by the developer.
This can be changed by editing .conkyrc and changing the section
```
TEXT
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}**Rhythmbox**${font}
```
to read...
```
TEXT
${color4}${font Terminus:style=Bold:size=14}@ ${font Terminus:style=Bold:size=11}**Banshee**${font}
```

---

