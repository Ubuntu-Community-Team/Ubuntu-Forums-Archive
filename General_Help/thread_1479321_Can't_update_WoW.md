---
title: "Can't update WoW?"
date: 2010-05-10
forum: General Help
---

### Post by Tzar Meathammer on 2010-05-10
I'm running Lucid Lynx, and I installed WoW and I want to see if I can run it on my new computer without upgrades and what not. I am running it with wine, and when it gets to the update screen I get this error box with nothing in it. I don't know what I'm doing, but I do know that this can be played on Ubuntu. Please help. Thank you in advance.

---

### Post by jerome1232 on 2010-05-10
The game does work fine, one suggestion would be to try launching Wow.exe directly instead of Launcher.exe.

---

### Post by emoguitarist06 on 2010-05-10
I second his answer

I tried installing WoW from online and it didn't work
I recommend the dvd

I followed this guide
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

at one point it froze but i just force quited it and started again
took a while... few hours
but now WoW runs flawlessly

---

### Post by Shakz on 2010-05-10
The above link ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ) works great. 

However also be aware that you can pull the "World of Warcraft" folder from any other machine if you already have it installed there and copy it to your linux machine. It will work fine. In vista its default install is the Public/games/ directory. Before I moved it from my win partition on my desktop to my laptop (full ubuntu) and followed the above link....just skipped the install part. 

YOU MUST DO THIS
edit the wtf/Config.wtf in your main  WoW directory. 

add this line

SET gxApi "opengl"

Its in the link too but if your like me and skim through tech docs.... I missed it first round.

---

### Post by Tzar Meathammer on 2010-05-10
Hah, WoW gets alot more responses than Guild Wars does. I am installing from the DVD. Do I have to make the new directory? Because it installs fine w/o it. I can't find a WoW.exe, but I'll look a little harder. I'm still Ubuntu retarded, seeing as I have only been using it for a month. I'll go read through that guide and post again when I get results.

---

### Post by Tzar Meathammer on 2010-05-10
ok I don't have anything in the WTF folder, so I can't add that line to it. It will launch up, but it won't do anything except sit on a black screen.

---

### Post by jerome1232 on 2010-05-10
Okay assuming your wow was installed in wine (so it's in the default location) try this

Press Alt+F2 type the following then hit run

```
wine "~/.wine/drive_c/Program Files/World of Warcraft/Wow.exe" -gl
```

---

### Post by Tzar Meathammer on 2010-05-10
OK so I found it and opened it, but it's just putting up a black screen, or just making everything really big... still nothing in the WTF folder. 

EDIT: OK it started working, gonna keep and eye on it

---

### Post by Tzar Meathammer on 2010-05-10
OK so it told me to update, so I tried, and then this happend.

---

### Post by jerome1232 on 2010-05-10
Huh okay what version of wine are you using? I'm using wine-1.1.42 and it works great.

type this in a terminal to find out.
```
wine --version
```

Maybe your wow files got corrupted somehow, in the main wow folder you should have a repair.exe, run that tell it to clear out your settings and check and repair everything, let that run, grab a cup of coffee and come back.


Another thought... what video card do you have, do you have the 3d accelerated drivers for it?

---

### Post by Tzar Meathammer on 2010-05-10
Well, I have a slim, so my graphics card is crap but I know I can run WoW, I hope... its an Intel Family Chipset G33/G31 and when I tried to install drivers for it, the install said "computer does not met minimum requirments. Setup will exit." and I am using wine 1.1.43

EDIT: Oh and when I try to run the repair, it does whats in the photo link 


[http://s863.photobucket.com/albums/ab195/TzarMeathammer/?action=view&current=Screenshot-6.png](http://s863.photobucket.com/albums/ab195/TzarMeathammer/?action=view&current=Screenshot-6.png)

---

### Post by jerome1232 on 2010-05-10
](*,)
](*,)

As far as I know that card gets 3d working out of the box with Ubuntu (easy test is if to see if compiz works, can you enable desktop affects? System-Prefrences-Apperance, Visual Effects, select normal or extra and see if it yells at your or not, if that works then you have 3d) So I don't think it's your graphics card.

Wow you have an old version of Wow right now :p I'm mostly out of idea's atm, I wish that repair utility would work. 

I'm running into 28 hours of being awake.

So um if someone doesn't help you figure this out by tomorrow I'll be back to beat my head against the wall a few more times. Good luck.

---

### Post by Tzar Meathammer on 2010-05-10
Ahh, thanks anyways. I know it's an old version, my friend decided to get me back into it, so I went straight from my disc, which is from 2007, oh and I already have the effects on advanced, so I guess I'm good there. This computer just hates me though.

---

### Post by Tzar Meathammer on 2010-05-10
I figured this would be helpful. with the SET gxApi "opengl"

I get error 132 as in an earlier SS and a huge thing of code that won't copy.

---

### Post by jerome1232 on 2010-05-13
I would just use the online installer, I know it works with *one* version of wine.


Maybe winehq's database has some hints. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)

---

### Post by Tzar Meathammer on 2010-05-15
Well well, I used the online installer, and I got it all installed, but I think I messed up my Wrath of the Lich King install. The first pic is what happens when I try to log in, the second is what happens when I try to re-install wrath of the lich king.

---

### Post by jerome1232 on 2010-05-15
perhaps some file was corrupted during the whole download install process. Try running that repair.exe file, it'll check all your files and redownload any that are found to be corrupt.

---

### Post by HiImTye on 2010-05-15
I use D3D for WoW because there's no hardware mouse for openGL and it works fine. WINE's D3D is an openGL implementation so you won't find much difference, except that your mouse won't lag around the screen (which is really annoying)

make sure you set your video memory in WINE
if you're using WINE without changing your wine prefix
```
regedit
```
and then navigate to HKEY_CURRENT_USER > Software > WINE > Direct3D and create a new key VideoMemorySize. set it to your video card's memory size in megabytes.
for instance, my video card has 512MB DDR2 so I set mine to 512.

if you can't update with the launcher then update with Wow.exe. Launcher.exe's ability to update is hit and miss. when Launcher.exe doesn't want to update just log in to Wow.exe and it will do the whole 'downloading updates..'

if your Wow.exe is corrupt then run Repair.exe. tell it to delete everything EXCEPT your saved variables (as you will lose your addons' preferences if you do delete those).

there's more but I currently let my account expire so I can't honestly log in right now to check my video settings, though I remember theres a few settings you don't want to enable as they will cause great lag and graphic corruption

---

