---
title: "shortcut for wine programs"
date: 2011-08-02
forum: General Help
---

### Post by Cnaeus on 2011-08-02
Since Lunbuntu does not have any graphical interface to create destktop shortcuts for programs, could someone tell me plz how can I create shortcuts for wine applications from empty files?

---

### Post by ajgreeny on 2011-08-02
If you are not aware of how .desktop files are produced, it may be easiest to right click on one for some other application, and click on the leafpad option you get.  The file will open as a txt file.  Here's the one for nautilus that I installed in my lubuntu install:-
```
 [Desktop Entry]
Name=nautilus
Exec=nautilus
Icon=nautilus
Terminal=false
Type=Application
StartupNotify=true
NoDisplay=true
OnlyShowIn=GNOME;LXDE
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.32.2.1
X-GNOME-Autostart-Phase=Desktop
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-GNOME-Provides=filemanager
X-Ubuntu-Gettext-Domain=nautilus
```many of those lines are superfluous, and only of use in the gnome desktop, so can be ignored, and I have deleted the lines from, and including "OnlyShowIn=GNOME;LXDE to the bottom.

That is for nautilus, but you can get the idea from that, and I'm sure you can sort something out..  You will need the same start line, then the name of the application or game, then for the executable in the Exec= line you will need ```
wine /home/username/.wine/full/path/to/application/exe/file
```

I don't use wine, but I know that in gnome it adds a wine sub-menu to the menu.  I presume from your question this does not happen in LXDE, but if it should do so, your problems are solved, of course, and you can just right click on the menu entry, add it to the desktop, then move that .desktop file wherever you want it to be.

---

### Post by Cnaeus on 2011-08-03
Well, I created a .desktop shortcut for notepad (programs in the menu has an option for it), and I thought rewriting the Exec= field would be enough. It isn't. After hitting enter on the shortcut, nothing happens, it doesnt react. Strange.

These were the lines that appeared after the names/comments section:

```
Exec=notepad
Terminal=false
Type=Application
Icon=wine-notepad
Categories=Wine-Programs-Accessories;
```

---

### Post by Morbius1 on 2011-08-03
> **Cnaeus said:**
> Since Lunbuntu does not have any graphical interface to create destktop shortcuts for programs, could someone tell me plz how can I create shortcuts for wine applications from empty files?
Your original premise is not correct. There is a GUI to create shortcuts but it's not invoked in a GUI way - ya gotta love linux :)

First, see if you have the following package installed - I've done so much tweaking I'm no longer certain it's there by default:
```
lxshortcut
```To create a desktop shortcut to notepad:
```
lxshortcut -o ~/Desktop/notepad
```Then a GUI starts that looks like the attachment. On yours the Name, Command, and Tooltip will be blank so just use the command that ajgreeny suggested and call it Notepad.

If you make a mistake and want to edit it use the following command:
```
lxshortcut -i ~/Desktop/notepad
```

---

### Post by ajgreeny on 2011-08-03
Thanks Morbius1.  I was not aware of that application in lxde either.  It looks very useful.  Unfortunately there is no "man lxshortcut" to assist, but no doubt there are posts on this forum if searched.

---

### Post by Morbius1 on 2011-08-03
There is a "lxshortcut --help" but all it lists as I remember is the "o" and "i" option and is worded in such a way that it's a miracle anyone figured out how to use it. I had seen the "o" option used somewhere and guessed the "i" stood for edit. 

You would think it would have given the user a fighting chance had they used "a" and "e" :)

---

### Post by Cnaeus on 2011-08-05
Um, I was aware of lxshortcut, but for some reason it didn't work for me. It simply didn't created any file on my desktop... I even tried it with sudo command... That's why I'm seeking for a way to create a shortcut from an empty file... :(

---

### Post by Morbius1 on 2011-08-06
Well, the only thing that lxshortcut will do is create a *.desktop file like the one it created for me:
> [Desktop Entry]
Encoding=UTF-8
Type=Application
Name=MyLan
Name[en_US]=MyLan
Icon=gnome-network-properties
Exec=pcmanfm /home/morbius/.gvfs
Comment[en_US]=
StartupNotify=trueSo to recreate this manually and pointing to notepad.exe:

From a terminal:
```
leafpad /home/morbius/Desktop/notepad.desktop
```Once in leafpad add the following content:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Notepad
Name[en_US]=Notepad
Icon=wine-notepad
Exec=?????
Comment[en_US]=
StartupNotify=true
```The only thing I don't know is the path.

Is it: [COLOR=Black]/home/morbius/.wine/drive_c/Program Files/notepad.exe

If it is then the "Exec=???" line would read:
[/COLOR]```
[COLOR=Black] Exec=wine "/home/morbius/.wine/drive_c/Program Files/notepad.exe"[/COLOR]
```

---

### Post by Cnaeus on 2011-08-08
Not working, sadly :( there must be some tricks with the exec line, but I dont know what it might be...

---

### Post by Morbius1 on 2011-08-08
What is the path to notepad.exe?
EDIT:
```
 whereis notepad.exe
```

---

### Post by mc4man on 2011-08-08
Possibly notepad isn't the best example, though I don't use Lubuntu so maybe things are different

Typically wine installs a wine wrapper script in /usr/bin for notepad so it can be started like any other binary, in this case just
notepad
So a simple desktop launcher would be 
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=wine-notepad
Name=notepad
Exec=notepad
StartupNotify=true
```
Noting that the launcher (.desktop) must be set to execute in permissions

For 'normal' installed .exes you can create launchers with several different Exec= lines, 2 examples here with same .exe
The only difference would be seen on something like Unity where the 2nd one produces the correct icon in the launcher, not a factor here.
```
[Desktop Entry]
Name=DVD Decrypter
Exec=wine "C:\Program Files\DVD Decrypter\DVDDecrypter.exe"
Type=Application
StartupNotify=true
Path=/home/doug/.wine/dosdevices/c:/Program Files/DVD Decrypter
Icon=/home/doug/.local/share/icons/48e9_dvddecrypter.0.png

```
or
```
[Desktop Entry]
Name=DVD Decrypter
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\DVD\\ Decrypter\\\\DVDDecrypter.exe
Type=Application
StartupNotify=true
Path=/home/doug/.wine/dosdevices/c:/Program Files/DVD Decrypter
Icon=/home/doug/.local/share/icons/48e9_dvddecrypter.0.png
```
To put some perspective I included the linux path in a Path= line, can be in the .desktop

As far as notepad - you could test if the wrapper script is working by simply using notepad in a terminal or run dialog  (Alt+f2 here

---

### Post by Cnaeus on 2011-08-10
Thank you Pc4Man, this is a very thorough guide :) but the shortcut still wont react. So I tried to run the "exec" lines (both of them, many times) in terminal, but it returned an error message: > wine: Bad EXE format for C:\Program Files\MyFolder\MyFile.exe
Ok, so I experimented a bit: installed a windows program, and pasted the exec line here. Well, it was frightening:
> Exec=env WINEPREFIX="/home/myusername/.wine" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/myusername/.wine/dosdevices/c:/users/Public/Start\\ Menu/Programs/MyFile/MyFile.lnk
:confused:

---

### Post by Morbius1 on 2011-08-10
So this does not work?
```
Exec=env WINEPREFIX="/home/myusername/.wine" wine "C:\Program Files\notepad.exe"
```Change "C:\Program Files\notepad.exe" to whatever the correct path is to the exe.

---

### Post by Cnaeus on 2011-08-10
It didn't work, but this time it gave an error message at least: > Failed to change to directory '/home/myusername/.wine/dosdevices/c:/Program Files/MyProgram/MyProgram.exe' (Not a directory)

No idea what it means... the path is all right, that is for sure.

---

### Post by mc4man on 2011-08-10
Then just use the method shown at the bottom of post 8, as in 
Exec=wine 'exact path to exe'
 So to get that AND test that the .exe works, open your file browser and navigate to the .exe
Then open a terminal, type in wine, hit the spacebar and then drag & drop your .exe into the terminal
That's your exact path, you can copy it out into your launcher (.desktop

To test the .exe then just press enter in terminal. If it runs the it will also run from the launcher

---

