---
title: "top panel missing (ocelot)"
date: 2012-01-11
forum: General Help
---

### Post by webcomm on 2012-01-11
In my main account, the panel in the upper right is missing.  That is,  the part of the panel that displays the username, and where you access  the system settings.  Also missing are the icons that normally appear in  that part of the panel -- battery indicator, volume, etc.  

All I see in the upper panel, on the left, is the following:
File Edit View Go Bookmarks Help

This has been a problem for a while now and I've been working around it  by using another account, but I'd like to get my main account fixed.  I  believe the problem began when I was messing with the compiz settings  manager.  I must have done something bad.  Is there some way I can  restore the main account to whatever the default settings are?

Also, the computer does not shutdown properly from the main account.  If I enter 'sudo shutdown now' in the terminal (there is no other way to shut down with the panel missing), the computer hangs and never finishes shutting down.  The last thing I see on the screen is something like "Shutting down apache2".  That's not the exact wording.

Ideas?

---

### Post by xc3RnbFO8P on 2012-01-11
Try in Terminal:
> unity --reset

---

### Post by PapaGary on 2012-01-11
Yep. And-

```
sudo shutdown -h now
```

---

### Post by webcomm on 2012-01-12
Ringi,

I don't think I'm using Unity.  When I try the reset command as you indicated, nothing changes.  Here's what I see in the terminal...

WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values
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
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

At that point the processing seems to stop, though there is no real indication it has stopped.  The cursor just sits there blinking on the last line, and doesn't show the prompt with my username.

---

### Post by Frogs Hair on 2012-01-12
What you see on the top panel can appear if Unity is not working properly . If you have selected Ubuntu during login you are using Unity .

When the process in the terminal seems to stop for a long time try closing the terminal . You may get a message indicating a process is still running , but close it anyway. 

If you need to reset Compiz and still have terminal access try the following .```
gconftool-2 --recursive-unset /apps/compiz-1 
```  
Then, open another terminal window, and run the following . 
```
unity --reset
```
If you remain without a desktop and only with  Nautilus options on the  bar at the top of the screen, go to the first terminal window, and run the following .
```
ccsm
```

I have used this method successfully .

---

### Post by webcomm on 2012-01-12
Frogs Hair,

Thanks for your response.  I went through the steps you suggested and there has been no change.  I still have only the nautilus menu in my main account.  My secondary account still works perfectly.

By the way, I presume that I should be working in the main account when I am trying to fix the main account.  That is, when I ran the commands suggested by Frogs Hair, I was in my main account -- the one that's broken.

Thanks,
Ryan

---

### Post by Frogs Hair on 2012-01-12
I don't have any further suggestions other than trying some of the things suggested at the link . [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by webcomm on 2012-01-12
Here's what fixed it:

Go into the compiz settings manager.  The command is ccsm.  In the Desktop section, enable the Ubuntu Unity Plugin.  I was prompted to decide how to resolve a number of conflicts regarding action keys.  I clicked the button on the right every time.  After resolving all conflicts, the missing elements in the top panel reappeared.  

Before I did any of that, I restarted LightDM as suggested at the tuxgarage link posted by Frogs Hair.  I don't know if that was also a factor in getting this fixed.

---

