---
title: "I killed unity (3d) by clicking &quot;set default settings&quot; in ccsm"
date: 2011-05-04
forum: General Help
---

### Post by nathema on 2011-05-04
Since i've touched the "set back to defaults" (or the like) in compiz configuration manager (CCSM), unity does not appear after logging in. I'm stuck with a complete blank screen, with my wallpaper and an mouse pointer.

I have attempted the following:
- restore unity by the steps in askubuntu.com: unity --reset
- reinstalled unity packages
- created another account, to see if the user configuration was the problem

Another hint:
- Ubuntu classic with effects shows my screens outside of the viewport and i'm unable to use them
- Ubuntu classic without effects operates properly

Any suggestions to reset compiz with unity. I actually like it.

Environment:
HP Compaq 8710p, Nvidia Quadra 320M, Natty 64bit updated to 4 may 2011, Unity 3d

---

### Post by imigueldiaz on 2011-05-04
> **nathema said:**
> Since i've touched the "set back to defaults" (or the like) in compiz configuration manager (CCSM), unity does not appear after logging in. I'm stuck with a complete blank screen, with my wallpaper and an mouse pointer.

I have attempted the following:
- restore unity by the steps in askubuntu.com: unity --reset
- reinstalled unity packages
- created another account, to see if the user configuration was the problem

Another hint:
- Ubuntu classic with effects shows my screens outside of the viewport and i'm unable to use them
- Ubuntu classic without effects operates properly

Any suggestions to reset compiz with unity. I actually like it.

Environment:
HP Compaq 8710p, Nvidia Quadra 320M, Natty 64bit updated to 4 may 2011, Unity 3d

Hi!

You could try 

```

unity --replace

```

--reset resets default configuration, and --replace replaces the current environment.

Hope it helps

Best

---

### Post by Martin_sensei on 2011-05-04
I had this too!  

Did the suggested fix work?

I ended up reinstalling the OS (bit overkill, but I had litterally just installed it, then tried to change some settings in ccsm, then everything seemed to break!)

---

### Post by nathema on 2011-05-04
> **imigueldiaz said:**
> Hi!

You could try 

```

unity --replace

```--reset resets default configuration, and --replace replaces the current environment.

Hope it helps

Best

I don't have control in the standard "Ubuntu" ("unity3d") session, so i tried this from the command line with the display environment variable set. 
It did something but no window elements appeared. One screen went black with mouse cursor available.

Within the "Ubuntu classic (no effects)" the top bar changed into the Unity style top bar (with the white ubuntu icon) but the sidebar did not appear. I also lost control over the userinterface. Nothing reacts.

With any linux distribution a reinstall is overkill, but as my opening post says, reinstalling the packages did nothing.

---

### Post by imigueldiaz on 2011-05-04
> **nathema said:**
> I don't have control in the standard "Ubuntu" ("unity3d") session, so i tried this from the command line with the display environment variable set. 
It did something but no window elements appeared. One screen went black with mouse cursor available.

Within the "Ubuntu classic (no effects)" the top bar changed into the Unity style top bar (with the white ubuntu icon) but the sidebar did not appear. I also lost control over the userinterface. Nothing reacts.

With any linux distribution a reinstall is overkill, but as my opening post says, reinstalling the packages did nothing.

Now you should restore both environments, Classic and Unity :(


Can you open a terminal on Classic?

then you can use:

```

metacity --replace

```

**But only on classic, not on Unity**


If you can't (perhaps Alt + F2 do the trick to run xterm), last time I could replace unity (never tried with classic) from normal tty console (ctrl + alt + F1) and running unity --replace command. I suppose you can do the trick login on classic and using the same procedure with metacity --replace.

The messages were bizarre (errors about DISPLAY etc) but unity returned.

---

### Post by nathema on 2011-05-04
> **imigueldiaz said:**
> Now you should restore both environments, Classic and Unity :(


Can you open a terminal on Classic?

then you can use:

```

metacity --replace

```**But only on classic, not on Unity**


If you can't (perhaps Alt + F2 do the trick to run xterm), last time I could replace unity (never tried with classic) from normal tty console (ctrl + alt + F1) and running unity --replace command. I suppose you can do the trick login on classic and using the same procedure with metacity --replace.

The messages were bizarre (errors about DISPLAY etc) but unity returned.

Performed in "Ubuntu classic (no effects)". Screen flashed but returned like standard "Ubuntu classic". 
```

nathema@Anathema:~$ metacity --replace
Xlib:  extension "RANDR" missing on display ":0.0".
Windowmanager waarschuwing: Treating resize request of legacy application 0x3a003c5 (dS+V BRS) as a fullscreen request

```
The last warning can be ignored, it's about resizing an Remmina open RDP connection.

---

### Post by nathema on 2011-05-04
As my OP writes, I have reinstalled the unity packages (remove/install configuration) to reset the unity settings in the system.

Which packages can i drop /install to reset the complete compiz/unity situation?

---

### Post by beew on 2011-05-04
Here is an easy way. See my post.

[http://ubuntuforums.org/showthread.php?p=10767103#post10767103](http://ubuntuforums.org/showthread.php?p=10767103#post10767103)

---

### Post by nathema on 2011-05-04
> **beew said:**
> Here is an easy way. See my post.

[http://ubuntuforums.org/showthread.php?p=10767103#post10767103](http://ubuntuforums.org/showthread.php?p=10767103#post10767103)
Unity is enabled in ccsm.

---

### Post by edm1 on 2011-05-04
You need to be able to open ccsm so log out and select Ubuntu Classic (No Effects) in the panel at the bottom once youve selected your user name. Login, open ccsm and enable unity plugin or ive uploaded my own compiz profile, which is pretty much the 11.04 default, which you can import under the ccsm preferences tab.

[http://dl.dropbox.com/u/20482058/Permanent/unity%20compiz.profile](http://dl.dropbox.com/u/20482058/Permanent/unity%20compiz.profile)

---

### Post by nathema on 2011-05-04
> **edm1 said:**
> You need to be able to open ccsm so log out and select Ubuntu Classic (No Effects) in the panel at the bottom once youve selected your user name. Login, open ccsm and enable unity plugin or ive uploaded my own compiz profile, which is pretty much the 11.04 default, which you can import under the ccsm preferences tab.

[http://dl.dropbox.com/u/20482058/Permanent/unity%20compiz.profile](http://dl.dropbox.com/u/20482058/Permanent/unity%20compiz.profile)

That worked!

Thanx!

---

### Post by edm1 on 2011-05-04
I've posted it as a bug report [here]("https://bugs.launchpad.net/unity/+bug/777024").

---

### Post by dahliar_ananda on 2011-07-11
Quote Reply to edm1
> 
You  need to be able to open ccsm so log out and select Ubuntu Classic (No  Effects) in the panel at the bottom once youve selected your user name.  Login, open ccsm and enable unity plugin or ive uploaded my own compiz  profile, which is pretty much the 11.04 default, which you can import  under the ccsm preferences tab.

[http://dl.dropbox.com/u/20482058/Per...compiz.profile]("http://dl.dropbox.com/u/20482058/Permanent/unity%20compiz.profile")
                                                                                                  
                                                                       [URL="http://ubuntuforums.org/newreply.php?do=newreply&p=10767173"]
[/URL]
i had the similar problem, thanks for your solution and profile.
it's works! :)

---

