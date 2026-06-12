---
title: "Installed game... where did it install to?"
date: 2011-03-23
forum: General Help
---

### Post by stephanmir on 2011-03-23
I installed a game called Rift. It installed a patched fine

The loader works fine, but when I click play it doesn't load. I'm assuming that I need to use the Wine loader with the direct play file. But I can't seem to find where this installed to when I go to the home directory. This is what the shortcut shows:

env WINEPREFIX="/home/stephan/.wine" wine C:\\Program\ Files\\RIFT\ Game\\riftpatchlive.exe 

I don't know where the C:\\Program\Files\\ is located in my gnome GUI. Anyone able to help?

- Gibson

---

### Post by ChipOManiac on 2011-03-23
C:\\Program Files\ Is In The ~/.wine/drive_c folder...

---

### Post by stephanmir on 2011-03-23
Ok cool thank you.

I found rift.exe and I am attempting to load the game directly using wine loader. It says Opening Rift.exe however it is cut short for some reason. Anyone able to assist with this issue?

Thanks

-Gibson

---

### Post by WorMzy on 2011-03-23
Have a look in the app's WineDB entry to see if anybody has any hints or tips to help you get it working.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22884](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22884)

---

### Post by stephanmir on 2011-03-23
Checked the hints and tips, wasn't able to find anything that can help.  I did everything they suggested with winetricks and also added the overrides. Also downloaded and copied:

cp mscoree.dll ~/.wine/drive_c/windows/system32/
cp streamci.dll ~/.wine/drive_c/windows/system32/

Which I click on the application to launch it, it doesn't do anything. Is this a direct x issue?

-Gibson

---

### Post by ChipOManiac on 2011-03-25
Try it this way, fire up the terminal and hit
```

wine "~/.wine/drive_c/Program Files/RIFT/Game/rift.exe"

```

If it gives any error output, post it here...

Note: Replace the parts after «/drive_c/» with the relevant path.

---

### Post by Kenjitamura on 2011-03-27
After I installed d3dx9 with winetricks I had to go into winecfg and edit *d3dx9_43 so that it's built-in and not native...that got it working for me...fps is pretty low but I have a low end graphics card.

Edit: Also I can't launch the rift.exe application directly, this is the command I use > padsp wine ".wine-rift/drive_c/Program Files/RIFT Game/riftpatchlive.exe" after it launches I login and select play. Note: I have it installed in its own bottle so if you didn't give it its own bottle you'll have to use > padsp wine ".wine/drive_c/Program Files/RIFT Game/riftpatchlive.exe"

---

### Post by d3v1150m471c on 2011-03-27
```

locate GameName.exe

```

---

