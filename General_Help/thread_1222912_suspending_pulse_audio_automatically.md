---
title: "suspending pulse audio automatically"
date: 2009-07-25
forum: General Help
---

### Post by diggedy on 2009-07-25
I currently play coun ter strike and pulse audio is causing me countless crashes. Ive considered removing it but im reading that it is an integral part of jaunty and im not sure how it will affect my system and all my other programs if I do.

I tried this solution  [http://forum.winehq.org/viewtopic.php?p=25107#25107](http://forum.winehq.org/viewtopic.php?p=25107#25107) and its worked but I have to stop the steam client (which auto starts when i log into ubuntu) change to the steam directory and run that command every time I want to play. Is there a command I can add to the steam.exe so that when ubuntu loads and steam starts, it automatically suspends pulse audio for steam.

Of course if I can disable pulse audio completely without any detrimental effects then this may be the better solution

---

### Post by ajgreeny on 2009-07-25
Have a look at pasuspender which is part of pulseaudio-utils.  It should be possible to run the windows game with wine by adding pasuspender before the wine command you use:
```
pasuspender wine "C: Program files/executable/path/game.exe"
```or something very similar.

---

### Post by diggedy on 2009-07-25
would i be possible for me to have a script run at startup for this? Im new to linux so I havent learned how to write them yet (although im trying to read up now but any help would be appreciated)

the commands i run are 

cd /home/name/.wine/drive_c/"Program Files"/steam/

then i run 

pasuspender -- wine ./Steam.exe

---

### Post by ajgreeny on 2009-07-25
I think you should be able to do it more simply just with a desktop launcher for the game.  Right click the empty desktop and choose "Create launcher".  In the dialog that appears leave Application in the Type Box.  In the Name box type Counter Strike, or whatever you want.  In the command box type ```
pasuspender wine /home/name/.wine/drive_c/"Program Files"/steam/stream.exe
```Add any comment you want in the bottom box, and give that a try.  By using the full pathway to the executable you don't need to navigate to the folder first to run it.

---

### Post by diggedy on 2009-07-26
that worked great, thanks :)

is there anyway I can make this launcher execute on startup? I tried adding it to startup items but it just opened the text

---

### Post by CatKiller on 2009-07-26
> **diggedy said:**
>  is there anyway I can make this launcher execute on startup? I tried adding it to startup items but it just opened the text

You could either add a startup application that has the same entries as the desktop launcher, or you could edit the file with ```
gedit Desktop/whateveryoucalledit.desktop
``` to add in the line ```
X-GNOME-Autostart-enabled=true
``` and then run ```
mv ~/Desktop/whateveryoucalledit.desktop ~/.config/autostart/
``` to make it run on startup.

---

### Post by ajgreeny on 2009-07-26
If you do it at startup, don't forget that it will mean that for that session you will have no pulseaudio, so will be in the same situation as removing pulseaudio from the machine, or nearly so, as when you close down counter strike pa should start up again.

---

### Post by diggedy on 2009-07-30
> **ajgreeny said:**
> If you do it at startup, don't forget that it will mean that for that session you will have no pulseaudio, so will be in the same situation as removing pulseaudio from the machine, or nearly so, as when you close down counter strike pa should start up again.


Do I actually need pulse audio or will my machine run fine without it?

---

### Post by CatKiller on 2009-07-30
> **diggedy said:**
> Do I actually need pulse audio or will my machine run fine without it?

You don't *need* it, but if you want to have sound then you'll need to use *something*, be that PulseAudio, ALSA, OSS, ESD, or whatever.

But pasuspender will only disable PulseAusdio while your game is running. When it finishes, PulseAudio will start again. From **man pasuspender**:
> 
**DESCRIPTION**
       _pasuspender_ is a tool that can be used to tell a local PulseAudio sound
       server to temporarily suspend access to the  audio  devices,  to  allow
       other  applications  access  them  directly.  _pasuspender_  will suspend
       access to the audio devices, fork a child process, and when  the  child
       process terminates, resume access again.

       Make sure to include -- in your _pasuspender_ command line before passing
       the subprocess command line (as  shown  above).  Otherwise  _pasuspender_
       itself  might end up interpreting the command line switches and options
       you intended to pass to the subprocess.

---

### Post by jerome1232 on 2009-07-30
IMHO if your sound card can do hardware mixing you don't need pulseaudio. If it can't you pretty much need it.

---

