---
title: "Launcher for Steam?"
date: 2010-05-21
forum: General Help
---

### Post by Joseph Schwenker on 2010-05-21
I used to have a Steam launcher in my Wine menu, but it no longer worked after I experimented with running Steam under PlayOnLinux.  I deleted the launcher, and am now unable to run Steam except by navigating to its executable manually in Nautilus.  I want a launcher script to add to my main menu.  Unforunately, whenever I create a Steam Menu under programs, the checkbox is unchecked, and does nothing.  Steam does not appear after I have added it.  Any help?  Just giving me the launcher would be find, though I would like to have a Steam menu, too.

---

### Post by -humanaut- on 2010-05-21
I can't offer you any advice with wine and steam but I thought I would let you know that there will be a Native Linux Steam by the end of Summer.

---

### Post by Joseph Schwenker on 2010-05-21
Yes, I know.  Isn't it great?  I sent a letter of joy to Valve.  I'm really happy about this.  I can't WAIT to play Gmod again with my friends, finally have that Windows vs Linux feud with my Steam friend resolved, and be able to use the voice chat and even hear micspamming again!  Gosh, after not using Windows for a year, I really miss micspamming.

---

### Post by -humanaut- on 2010-05-21
> **Joseph Schwenker said:**
> Yes, I know.  Isn't it great?  I sent a letter of joy to Valve.  I'm really happy about this.  I can't WAIT to play Gmod again with my friends, finally have that Windows vs Linux feud with my Steam friend resolved, and be able to use the voice chat and even hear micspamming again!  Gosh, after not using Windows for a year, I really miss micspamming.

lol, Yeah dude im stoked about Steam coming to Linux finally I've just been a console gamer since I started using Linux but I would love to finally get back into PC games again Have you tried Alien Arena yet?

---

### Post by dtfinch on 2010-05-21
A problem with launchers and most programs on wine is that they neglect to "cd" to the correct directory. I usually end up creating a shell script to do it, making it executable, and pointing the launcher to the shell script.
My launcher for Portal on Steam looks like.
```
#!/bin/sh
cd "/home/david/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam"
env WINEDEBUG=-all WINEPREFIX="/home/david/.PlayOnLinux/wineprefix/Steam" wine Steam.exe -applaunch 400 -dxlevel 81
```

To just launch Steam alone, without running a game, you'd leave off the "-applaunch 400 -dxlevel 81". And you'd want to change the home directory to match yours. The "-dxlevel 81" was to fix some slowness I had, but it lowers the quality a bit. To launch a different game, change the 400 to whatever id goes with that game. I think gmod is 4000. A long list of ids is at [http://developer.valvesoftware.com/wiki/Steam_Application_IDs](http://developer.valvesoftware.com/wiki/Steam_Application_IDs)

---

### Post by Joseph Schwenker on 2010-05-21
> **dtfinch said:**
> A problem with launchers and most programs on wine is that they neglect to "cd" to the correct directory. I usually end up creating a shell script to do it, making it executable, and pointing the launcher to the shell script.
My launcher for Portal on Steam looks like.
```
#!/bin/sh
cd "/home/joseph/.wine/wineprefix/Steam/drive_c/Program Files/Steam"
env WINEDEBUG=-all WINEPREFIX="/home/joseph/.wine/wineprefix/Steam" wine Steam.exe
```

To just launch Steam alone, without running a game, you'd leave off the "-applaunch 400 -dxlevel 81". And you'd want to change the home directory to match yours. The "-dxlevel 81" was to fix some slowness I had, but it lowers the quality a bit. To launch a different game, change the 400 to whatever id goes with that game. I think gmod is 4000. A long list of ids is at [http://developer.valvesoftware.com/wiki/Steam_Application_IDs](http://developer.valvesoftware.com/wiki/Steam_Application_IDs)

Hmm... I modified your script and made the changes that you see above.  I put it into a file in /home/joseph/Documents/Miscellaneous Text Files/Steam Launcher, and put an "sh" before that in the menu editor.  Steam isn't launching, though.  What should I put into the command field?

---

### Post by Joseph Schwenker on 2010-05-21
> **-humanaut- said:**
> lol, Yeah dude im stoked about Steam coming to Linux finally I've just been a console gamer since I started using Linux but I would love to finally get back into PC games again Have you tried Alien Arena yet?

No, I haven't. Does it have microphone support?  Currently, Blood Frontier is my favorite Linux multiplayer game, and Penumbra is my favorite single player.  World of Goo is good, too, though.

---

### Post by Extol11 on 2010-05-21
> **-humanaut- said:**
> I can't offer you any advice with wine and steam but I thought I would let you know that there will be a Native Linux Steam by the end of Summer.

Link? I've not seen anything official yet.

---

### Post by Joseph Schwenker on 2010-05-21
[http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html](http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html)

"Valve has also confirmed that it will make Steam available to Linux users in the coming months."

Besides that, there is evidence everywhere, in the Mac Steam launcher, in the Left 4 Dead Demo files, etc.  Steam IS coming to Linux.  It's probable to the point that there's not much doubt.  Valve has not posted it on their website yet, but it was confirmed somehow by Telegraph UK.  In fact, something's been leaked or released, because Phoronix has screenshots of a partial UI rendering natively on Ubuntu.  [http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1)

---

### Post by dtfinch on 2010-05-21
If you run the sh script from the terminal, do you get any errors? Did you mark it as executable in the properties/permissions?

---

### Post by Joseph Schwenker on 2010-05-21
> **dtfinch said:**
> If you run the sh script from the terminal, do you get any errors? Did you mark it as executable in the properties/permissions?

I just marked it as executable now, and it still doesn't work.  This is the terminal output:
```
joseph@joseph:~$ sh /home/joseph/Documents/Miscellaneous\ Text\ Files/Steam\ Launcher 
cd: 2: can't cd to /home/joseph/.wine/wineprefix/Steam/drive_c/Program Files/Steam
wine: chdir to /home/joseph/.wine/wineprefix/Steam
 : No such file or directory
joseph@joseph:~$
```

---

### Post by dtfinch on 2010-05-21
Maybe that's the wrong folder. You'll have to change it to the Steam location on your system.

---

### Post by Joseph Schwenker on 2010-05-21
> **dtfinch said:**
> Maybe that's the wrong folder. You'll have to change it to the Steam location on your system.

My Steam is located in /home/joseph/.wine/dosdevices/c:/Program Files/Steam/Steam.exe

How should I put that into the file?

---

### Post by dtfinch on 2010-05-22
If the c: is just a symbolic link to drive_c in .wine, I'd try this
```
#!/bin/sh
cd "/home/joseph/.wine/drive_c/Program Files/Steam"
env WINEDEBUG=-all WINEPREFIX="/home/joseph/.wine" wine Steam.exe
```

You might be able to get away with just "wine Steam.exe" for the 3rd line. I had the "WINEDEBUG=-all" to disable debugging messages that slow things down if a game starts triggering them on every frame, and the WINEPREFIX was because PlayOnLinux installed to a new wine folder instead of using the default .wine, so wine had to be told to use the new folder.

Before I had assumed you were trying to run the Steam install created by PlayOnLinux. On mine it put it in the .PlayOnLinux folder

---

### Post by Joseph Schwenker on 2010-05-22
Thanks!  That script works, though I still am not sure what to put in the "command" field of Alacarte.  I want to create an entry in the menu for Steam.  What should I put in?

---

### Post by -humanaut- on 2010-05-22
> **Joseph Schwenker said:**
> No, I haven't. Does it have microphone support?  Currently, Blood Frontier is my favorite Linux multiplayer game, and Penumbra is my favorite single player.  World of Goo is good, too, though.

Thanks for giving that Link.

Alien Arena does have Microphone support. Basically its a better Quake III it's an I.D. product It's frantic but pretty awesome I haven't played in long time though. I'm gonna give that Quake Live a try here in a few days that looks pretty awesome.

---

### Post by Extol11 on 2010-05-22
> **Joseph Schwenker said:**
> [http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html](http://www.telegraph.co.uk/technology/apple/7715209/Steam-for-Mac-goes-live.html)

"Valve has also confirmed that it will make Steam available to Linux users in the coming months."

Besides that, there is evidence everywhere, in the Mac Steam launcher, in the Left 4 Dead Demo files, etc.  Steam IS coming to Linux.  It's probable to the point that there's not much doubt.  Valve has not posted it on their website yet, but it was confirmed somehow by Telegraph UK.  In fact, something's been leaked or released, because Phoronix has screenshots of a partial UI rendering natively on Ubuntu.  [http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1](http://www.phoronix.com/scan.php?page=article&item=valve_steam_announcement&num=1)

I don't know. I'll remain skeptic until valve actually says something on their website. I don't want to get my hopes up.

---

### Post by Joseph Schwenker on 2010-05-30
I still need a launcher script for Steam!  Steam is located in: /home/joseph/.wine/dosdevices/c:/Program Files/Steam/Steam.exe

---

### Post by Joseph Schwenker on 2010-05-31
bump

---

### Post by dtfinch on 2010-05-31
You should be able to just put the full path of the .sh script in the command field of the launcher.

---

### Post by Joseph Schwenker on 2010-05-31
I tried that, but it didn't work.  I'll try it again soon.

---

### Post by Joseph Schwenker on 2010-06-15
I'm having a problem.  If I create a menu called "Steam" under Wine>Programs, it is immediately checked off, and it always stays so, even if I uncheck it.  How can I stop this behavior?

---

### Post by Joseph Schwenker on 2010-06-15
OK, the launcher script solved the problem, though I still would like a Steam under Wine>Programs.

---

### Post by Joseph Schwenker on 2010-08-11
It's weird that I am unable to add any new directories entitled Steam, even manually.  However, I'll just mark this thread as solved.
It must be some corrupt file or something, though nothing ever appears in the directory.

---

