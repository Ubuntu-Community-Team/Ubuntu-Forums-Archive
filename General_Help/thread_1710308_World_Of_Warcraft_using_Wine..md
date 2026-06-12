---
title: "World Of Warcraft using Wine."
date: 2011-03-19
forum: General Help
---

### Post by TrickStyle on 2011-03-19
I have a problem with WoW using Ubuntu 10.10 and Wine 1.2.2.

I can run it. And I have everything, and I do mean everything, except the skins.

The login screen has everything except the background animation (of the Dark Portal (2.4.3. 8606), the account screen also doesn't show the animated background, as much as the characters also.

This is in Wine's Direct3D mode. When using gfxapp=opengl (or similar) in the wowroot/WTF/config.wtf file, the only difference is that now I have particles.

I have an AMD Athlon 64bit processor and an ATI video card, if that is of any concern (as I have somewhere read that ATI doesn't work with Wine (or similar)).

So, I am asking: WTF?

---

### Post by gyussz on 2011-03-19
I can't be sure, but you're using a very very old WoW client, I guess that could be a problem.

EDIT: some detailed info about 2.x clients: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6482](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6482)

---

### Post by Dagonath on 2011-03-21
Hi

I have a problem too with wine. When I run wow with d3d screen flashes/blinks and when I run it in opengl it crashes, outputing the Memory could not be "read" error. No use of using crossover games since it uses wine engine and with Cedega there are some Locale problems. I'm running Ubuntu 10.10 and I'm using wine 1.2.2 and Crossover 10.1.0. 
I've been trying to figure it out for 2 days and still no luck.

---

### Post by gyussz on 2011-03-21
By running in opengl you mean the config.wtf file in the WTF folder contains the following line, exactly like this:
```
SET gxApi "opengl"
```
Wine should be on Windows 7 mode to run correctly (according to my experiences). Open the Wine Configuration windows (winecfg) and set Windows version to Windows 7 on the Applications tab.

If still no luck, try to clear the config.wtf file (only leave the gxApi one there). 

Check [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549) for more information.

---

### Post by Dagonath on 2011-03-21
It still crashes.

You can see the contents of my config file here:
```
This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\wow\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:69063B1B

The instruction at "0x69063B1B" referenced memory at "0x00004294".
The memory could not be "read".


WoWBuild: 12340
Settings: 
SET accounttype "LK"
SET uiScale "0.77999997138977"
SET useUiScale "1"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET coresDetected "2"
SET hwDetect "0"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "3"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "727"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET mouseSpeed "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET gameTip "14"
SET gxResolution "800x600"
SET gxTripleBuffer "1"
SET componentTextureLevel "9"
SET ffxDeath "0"
SET ffxGlow "0"
SET gxRefresh "60"
SET gxFixLag "0"
SET weatherDensity "0"
SET checkAddonVersion "0"
SET Sound_OutputQuality "0"
SET Sound_EnableMusic "0"
SET Sound_EnableSFX "0"
SET Sound_EnableAmbience "0"
SET gxWindow "1"
SET locale "enUS"
SET realmList "logon.molten-wow.com"
SET realmName "Neltharion x12"
SET gxApi "opengl"
```


Link to full report: [http://www.upload.ee/files/1211949/fullreport.txt.html](http://www.upload.ee/files/1211949/fullreport.txt.html)

---

### Post by MagnaFX on 2011-03-22
Start world of warcraft in the terminal. use wine (yourwowdirectory)/WoW.exe -opengl

---

### Post by Dagonath on 2011-03-22
Doesn't work. 

I reinstalled my graphic drivers and still no luck. :\

---

### Post by Dagonath on 2011-03-24
It just gone worse. Now it crashes with d3d settings too. Same error as before with opengl

---

