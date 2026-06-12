---
title: "Resetting Compiz/Unity to default settings"
date: 2011-11-12
forum: General Help
---

### Post by dnr1128 on 2011-11-12
This evening while trying to get my dash to be on the bottom of my screen, instead of on the left side, I unchecked some boxes and royally messed up the interface.  Now, whenever I'm in normal Unity (I'm in 2d at the moment, its working fine), the dash doesn't appear, the desktop is all messed up (no menus at the top, etc).  Is there a way that I can reset the compiz and unity settings to the default install settings to reverse whatever i did?

---

### Post by TimEnid on 2011-11-12
this has been an ongoing issue lately. the fix is in this thread
ubuntuforums.org/showthread.php?t=1871081&page=3

---

### Post by dnr1128 on 2011-11-12
Read through it, tried purging compiz, then reinstalling it, reinstalling unity, and resetting unity, all from the recovery console, but I'm still getting a ton of errors during the reset process.

---

### Post by stinkeye on 2011-11-12
From your 2d session run
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```

You can't change the launcher position unless you use a plugin hack which is buggy.
Reinstalling is pointless when its your config files at fault.

---

### Post by dnr1128 on 2011-11-12
> **stinkeye said:**
> From your 2d session run
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```

You can't change the launcher position unless you use a plugin hack which is buggy.
Reinstalling is pointless when its your config files at fault.

Did that, restarted and booted into normal ubuntu.  The launcher is at the bottom.  The main problem I'm seeing now is that programs, like Chrome, aren't seeming to recognize the limits of the screen.  Also, when i'm in a program, and put my mouse cursor at the bottom of the screen, the launcher doesn't pop up.  

After running the above command, do I need to reset unity?  Whenever I've done that, its run into a lot of "file not found" and then just hangs.  The the same problem everybody else is having?

---

### Post by stinkeye on 2011-11-13
How did you get the launcher at the bottom?

---

### Post by dnr1128 on 2011-11-13
> **stinkeye said:**
> How did you get the launcher at the bottom?

I have no idea.  doesn't matter where I select it to hide, it goes to the bottom.

---

### Post by stinkeye on 2011-11-13
> **dnr1128 said:**
> I have no idea.  doesn't matter where I select it to hide, it goes to the bottom.
Can you post a screenshot of the launcher at the bottom?

---

### Post by dnr1128 on 2011-11-13
> **stinkeye said:**
> Can you post a screenshot of the launcher at the bottom?

[IMG]http://i947.photobucket.com/albums/ad317/David_Ryerson/Screenshotat2011-11-12230118.png[/IMG]

took this last night.  The launcher is at the bottom, with a box opened trying to put it on the side.

---

### Post by stinkeye on 2011-11-13
Did you install the unityshell hack?
eg [**_[COLOR="DarkRed"]http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html[/COLOR]_**]("http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html")

---

### Post by dnr1128 on 2011-11-13
Looks like that's what the problem was.  I had installed it yesterday evening, but then removed it (or so I thought).  

I typed in the remove command, and it said there was no such file.  So, I reinstalled it, figuring that would overwrite any orphan files that were remaining.  Then I removed it.  That went fine.  But when I logged out and then logged back in (doing all this in unity 3d), unity was hanging up and the only way out was a hard reboot.  AFter going through that a couple times, I did a hard reboot into recovery, and it fixed some errors (couldn't see what they were).  Appears to be working fine now, although I actually like the 2d.  Works a little bit faster.  

Thanks for the help!

---

### Post by stinkeye on 2011-11-13
> **stinkeye said:**
> How did you get the launcher at the bottom?
> **dnr1128 said:**
> I have no idea.  doesn't matter where I select it to hide, it goes to the bottom.
That's fine and I'm glad it's fixed but don't you think it"s a good idea to divulge
any obviously relevant info.
I wasted a couple of hours the other night trying to help someone fix unty
only to find out in the end they had actually uninstalled unity.
Luckily I knew about this hack and didn't waste another 2-3 hours.

---

