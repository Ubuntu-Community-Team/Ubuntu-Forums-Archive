---
title: "World of Warcraft+Wine"
date: 2006-06-08
forum: General Help
---

### Post by plastik_mang on 2006-06-08
Alright. I'm reasonably new to ubuntu. But i do have some experience with Linux.
So, im trying to run World of Warcraft in wine. 
1. I would like to get rid of the background downloader starting up.
2. Whenever i try to edit my settings wow crashes. If i start wow in direct3d mode and try to change a setting, wow exits to the desktop, and i can move my mouse, but the rest of my desktop seems completely frozen.

I can run WoW fine, but i would really like to be able to change my UI scale, or to fine tune everything.

If someone could help me i would greatly appreciate it. If someone has gotten WoW to work on highest settings, i would appreciate it if you could post your config.wtf file.

Many thanks.

---

### Post by conro on 2006-06-08
although i am morally against it, i have been using transgaming's cedega to play wow on my gentoo box... it works really well, even with opengl..

with the older version of cedega, i was having similar problems with wow crashing when updating my settings.. i ended up having to copy my roommates config.wtf file to get things set up the way that i wanted, but the most recent version of cedega seems to fix this. 

i can post my config.wtf file when i get home, but you should look into using cedega as you might get better perfomance then through wine.. i get better frame rate running wow through cedega then i do running it natively in windows :)

---

### Post by GmAz on 2006-06-08
To remove that background downloaded, do this.  Next time it opens up and you get taken to the window, go to the File menu and go to preferences.  Uncheck the box that says "Enable Background Downloading".  Thats it.  Same as in Windows.  Either that, or delete the update file form the WoW directory.

---

### Post by plastik_mang on 2006-06-08
Alright, disregard what i said previously. I got WoW working almost flawlessly. I can't get completely smooth edges, and my fps won't go higher than 30. In windows, i have gotten up to 90 fps, any solutions?

---

### Post by conro on 2006-06-09
do you have opengl enabled?
try ```

wine -gl -gldrv Default WoW.exe

```

---

### Post by plastik_mang on 2006-06-09
[QUOTE=conro]do you have opengl enabled?
try ```

wine -gl -gldrv Default WoW.exe

```[/QUOTE]
Yes, i do have WoW running with opengl.

When i run the code, i get this 
```
gabe@Yarbuntu:~/.wine/drive_c/Program_Files/World_of_Warcraft$ wine -gl -gldrv Defaul WoW.exe
wine: could not load L"c:\\windows\\system32\\-gl.exe": Module not found

```

---

### Post by clarke.rainey on 2006-06-09
[QUOTE=plastik_mang]Alright, disregard what i said previously. I got WoW working almost flawlessly. I can't get completely smooth edges, and my fps won't go higher than 30. In windows, i have gotten up to 90 fps, any solutions?[/QUOTE]


I have the exact same problem... will not go above 30 that I have been able to see put has no problem dropping to 9 at the lowest... in windows it was 3 times faster... so about 30-90fps... I have direct rendering and 3d acceleration running and it is running in OpenGl... it would be amazing if I could get that fixed...

---

