---
title: "make a link to a .exe file"
date: 2011-05-22
forum: General Help
---

### Post by then_dude on 2011-05-22
hello,

i got a small problem: i have some old software that used to run under windows.
now i run it under wine, and it does just fine. but i cannot make a link to my desktop. 

when i go to the file in the directory,  i choose right mousclick and then make link. 
then i copy the link to the desktop. but when i run the link from the desktop: i get errors: all bunch of files were not found. It seems like the link is actually the exe file itself ? or that the link execute the exe file at the directory of the place where the link is (that is the desktop directory)

can anybody help me out on this ? 

thanks so much
friendly greetz

---

### Post by lmn. on 2011-05-22
I think if you use playonlinux it has an option to add to the menu/desktop
although wine can probably do this too..

---

### Post by mc4man on 2011-05-22
You probably need a better Exec= line in the launcher
Easiest way is in a text editor though you can from the properties of the launcher (.desktop

For text editor just open gedit - drag and drop the launcher on to

2 ex. using ImgBurn - one or the other or both should work, adjust blue to match your username and location and program name

```
env WINEPREFIX="/home/[COLOR="Blue"]doug[/COLOR]/.wine" wine C:\\\\[COLOR="Blue"]Program[/COLOR]\\ [COLOR="Blue"]Files[/COLOR]\\\\[COLOR="Blue"]ImgBurn[/COLOR]\\\\[COLOR="Blue"]ImgBurn[/COLOR].exe

```
or 
 ```
wine "C:\\[COLOR="Blue"]Program[/COLOR][COLOR="Blue"] Files[/COLOR]\\[COLOR="Blue"]ImgBurn[/COLOR]\\[COLOR="Blue"]ImgBurn[/COLOR].exe"

```

or you could probably use  - leave any spaces in path like in Program Files

wine "/exact/path/to/the/whatever.exe"

Here is an example of my .desktop for ImgBurn, a bit more than you'll need, just to show format of Exec=
```
[Desktop Entry]
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\ImgBurn\\\\ImgBurn.exe
Icon=/home/doug/.local/share/icons/b06c_imgburn.0.png
Name=ImgBurn
Path=/home/doug/.wine/dosdevices/c:/Program Files/ImgBurn
StartupNotify=false
Type=Application
```

---

### Post by then_dude on 2011-05-23
thanks

now i understand how to make a launcher to that kind of software.

but there is something strange, it still doesn't work. 
the cursus show the busy symbol but the software is never loaded. 
i don't get any error messages, but nothing happens, and after a few seconds the cursus is back to normal. 

what couldthis be ?

thanks

I GOT IT: i had to leave a space after \ if the directory is in two words
thanks so much

---

### Post by linuxinstalledfromhdd on 2011-05-23
Isn't this an incomplete address to file:

wine "C:\\[COLOR=Blue]Program[/COLOR][COLOR=Blue] Files[/COLOR]\\[COLOR=Blue]ImgBurn[/COLOR]\\[COLOR=Blue]ImgBurn[/COLOR].exe"

---

### Post by mc4man on 2011-05-23
> **linuxinstalledfromhdd said:**
> Isn't this an incomplete address to file:

wine "C:\\[COLOR=Blue]Program[/COLOR][COLOR=Blue] Files[/COLOR]\\[COLOR=Blue]ImgBurn[/COLOR]\\[COLOR=Blue]ImgBurn[/COLOR].exe"

In that Ex. no, it's "..."  and that, (Program Files), is the actual name of the dir.
The previous Ex. isn't quoted so it is Program\\ Files instead (using window's path of \

---

