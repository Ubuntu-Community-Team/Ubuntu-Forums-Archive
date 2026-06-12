---
title: "Wine application shortcuts in 12.04"
date: 2012-08-02
forum: General Help
---

### Post by Paresh on 2012-08-02
Hi guys

Is there any way of getting a shortcut to a wine application?

I have this .desktop file
```
[Desktop Entry]
Name=Mp3 Tag
Exec=wine ~/.wine/drive_c/Program\ Files/Mp3tag/Mp3tag.exe
Icon=
Type=Application
```

the exec line works in bash, so I know it's correct, but I get no response when I click the desktop file.

I have tried creating a link to the executable I want, but that only works in the same directory as the executable.  If I move it to any other directory, I get no response at all.

I would like to launch this app from my desktop, but I don't know what else to try.

Hope someone can help.

Paresh

---

### Post by Vaphell on 2012-08-02
i looked at the .desktop file that was created by a game installer on my 10.04
its exec line looks like this:
```
Exec=env WINEPREFIX="/home/yourname/.wine" wine "C:\\Program Files\\AppDir\\executable file.exe"
```

user specific .desktop files are located in ~/.local/share/applications

---

### Post by mc4man on 2012-08-02
As noted above you can quote the path, (either linux or window formatting) in which case no need to escape spaces in .
or
Use windows formatting using \\\\ for directories & \\ for spaces. 
So 2 additional examples would be 
```
Exec=wine "~/.wine/drive_c/Program Files/Mp3tag/Mp3tag.exe"
```

```
Exec=wine C:\\\\Program\\ Files\\\\Mp3tag\\\\Mp3tag.exe
```
Sometimes it doesn't hurt to add a Path= line, though not usually needed, it is linux path to where the .exe is, like this where blue is replaced with your username - 
```
Path=/home/[COLOR="Blue"]username[/COLOR]/.wine/dosdevices/c:/Program Files/Mp3tag

```
Also doesn't hurt to have an icon, though again maybe not 100% needed.
For icons in /usr/share/pixmaps, /usr/share/app-install/icons, or in the install folder of your wine app you only need the name of the icon, otherwise full path.

(- the properties > permissions of a launcher should show executable for clicking on to launch

---

### Post by Paresh on 2012-08-02
I created the .desktop file by hand and tried the command in bash to make sure it worked before putting it in the .desktop file.

so ```
wine ~/.wine/drive_c/Program\ Files/Mp3tag/Mp3tag.exe
``` works in bash, but not in the .desktop file and ```
wine C:\\\\Program\\ Files\\\\Mp3tag\\\\Mp3tag.exe
``` works in the .desktop file, but not in bash.

Strange ...

Btw, thanks for the help guys.

---

### Post by LewisTM on 2012-08-02
The tilde ~ is a variable that gets interpreted and expanded by bash to your home location. Rarely will a DE do that for .desktop files i.e. it will not invoke bash to interpret the command, just execute it.
Consequently 
```
wine /home/<yourname>/.wine/drive_c/Program\ Files/Mp3tag/Mp3tag.exe
```
should work as well as 
```
bash -c "wine ~/.wine/drive_c/Program\ Files/Mp3tag/Mp3tag.exe"
```
and 
```
bash -c "wine $HOME/.wine/drive_c/Program\ Files/Mp3tag/Mp3tag.exe"
```

Cheers!

---

