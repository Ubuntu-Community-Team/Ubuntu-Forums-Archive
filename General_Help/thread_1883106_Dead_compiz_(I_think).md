---
title: "Dead compiz (I think)"
date: 2011-11-18
forum: General Help
---

### Post by the_blue_box on 2011-11-18
I have just moved my Ubuntu HD from one computer to a new better one. All was fine every thing worked but then I ran the updated manager (it hadn't been connected to the internet for a while so there were over 120 updates) and after the reboot all I got was my wallpaper and a menu along the top of my monitor with:

File Edit View Go Bookmarks Help

I have tried 
```
compiz --replace
```
but I just get this...
```
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3800580

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3800572

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3800564

```

If I login with unity 2d root or guest all is normal.

So what the hell has gone wrong and how do I fix it?

If anyone has a solution it would make my day.

Thanks
[COLOR="Navy"]BB[/COLOR]

---

### Post by the_blue_box on 2011-11-18
I don't want to bump but I really need an answer I don't like using Ubuntu 2D :(

Sorry for bumping
[COLOR="Navy"]BB[/COLOR]

---

### Post by grahammechanical on 2011-11-18
I found this link for you:

[http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal]("http://askubuntu.com/questions/38579/how-do-i-restart-an-unity-session-from-the-terminal")

Note the simple command unity.

I think it is Unity that has crashed. Do you have CCSM (CompizConfigurationSettinsManager) installed? Is the Unity plugin enabled?

Regards.

---

### Post by Cavsfan on 2011-11-18
Also, I wanted to throw this in. My compiz quit working a couple of weeks ago and it ended up being caused by 
my nvidia video driver. I installed the latest and the problem was solved.

**grahammechanical** probably has a better idea. Just thought I would mention this.

---

### Post by the_blue_box on 2011-11-18
I had already tried switching off my nvidia video driver, but thanks all the same :)

Thanks grahammechanical :KS :) Yes the Unity plugin had switched itself off (I don't know how) :rolleyes: 

Thanks again :)
[COLOR="Navy"]BB[/COLOR]   

PS. How can I change this thread to "solved"?

---

### Post by Cavsfan on 2011-11-21
> **the_blue_box said:**
> PS. How can I change this thread to "solved"?

Glad you got it working! :)

To mark this thread as solved, just click on [COLOR=Red]Thread tools[/COLOR] at the top and then at the bottom of the list click on "Mark this thread as solved".

---

### Post by the_blue_box on 2012-01-02
This has now happened again after playing with Ubuntu tweaks :cry:

I now can't use "Ubuntu" "Ubuntu 2d" or the "guest session" I'm currently on minimal gnome shell (standard gnome shell isn't working at all) lots of things aren't working.

I have to fix this. 
I've got a lot work to do.
I'm at the end of my tether.
I can't afford to reinstall.

Please can someone help

---

### Post by the_blue_box on 2012-01-02
Oh yes and the Unity plugin is enabled.

---

