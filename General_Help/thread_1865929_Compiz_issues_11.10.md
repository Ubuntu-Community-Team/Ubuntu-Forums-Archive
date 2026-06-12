---
title: "Compiz issues 11.10"
date: 2011-10-20
forum: General Help
---

### Post by coldcrow on 2011-10-20
I'm having issues with 11.10.  When I run unity --reset  I am getting some warnings.

> compiz (core) - Warn: unhandled ConfigureNotify on 0x120009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-20 17:21:05 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-20 17:21:07 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-10-20 17:21:07 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
compiz (core) - Warn: unhandled ConfigureNotify on 0x1200161!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.


---

### Post by desero on 2011-10-20
I am having the same problem. I installed CCSM and was going to disable the MT Handles (because when I put my mouse over the scrollbar the handles would appear and I'd resize the window instead of scrolling down!).  When reviewing the options in CCSM I clicked the Properties button and everything froze, so I killed the process and when I returned to the desktop Unity was broken, no sidebar or anything, just Nautilus.  Now I have tried
```
sudo apt-get purge unity && sudo apt-get install compiz unity ubuntu-desktop
```
wich should have just removed everything along with the configuration files and reinstalled the packages. When I logged in again, no Unity. (However it seems to work on the Guest account!).  I have also tried:
```
gsettings reset-recursively com.canonical.Unity
unity --reset
unity --replace
```

None of which seem to work.  The last two give me the same warning message you got. Found multiple threads about a similar problem, all suggesting the same solution which is to reset unity, but that just doesn't work for me.  Found no solution.

---

### Post by neptunecentury on 2011-10-20
Hello,
I am having a similar issue. The new Unity was working, but then suddenly and completely disappeared and I only see a small menu at the top for "File Edit View" etc.. but no clock, no side panel no power button. I tried restarting my computer many times but no luck.

So, I tried resetting unity with unity --reset, but just got a message saying:

> unity --reset
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
OpenGL Warning: No pincher, please call crStateSetCurrentPointers() in your SPU
Initializing opengl options...done
OpenGL Info: Using XSHM for GLX_EXT_texture_from_pixmap
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
compiz (core) - Warn: no exact match for ConfigureNotify on 0x1c00092!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0xa14bd10
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 1920
compiz (core) - Warn: height: 976
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

Any ideas?
If I log in with Ubuntu 2d, it works, but I cannot use the new version.

---

### Post by PaulInBHC on 2011-10-20
The Unity plugin box is not checked in CCSM by default. Login and select unity 2d. Open CCSM and check the Unity plugin box. Log out and back in with Unity selected.

---

### Post by neptunecentury on 2011-10-20
Thank you!
That was the resolution for me.

---

### Post by ctdahle on 2011-10-20
I was having the same issue: Unity disappeared when I installed CCSM, leaving only Nautilus available on my desktop.

This thread did solve the problem for me, but I wonder what complete beginners who do not know how to even restart their machines with out a GUI will do when they confront the same problem...write off Linux and Ubuntu I suspect.

Booting into Unity 2d and selecting the Unity plugin in CCSM did solve the problem, but...

I was especially troubled that doing so initiated a series of configuration choice prompts which had no meaning for me. I chose what I thought to be the defaults, but since I only had about 4 hours experience with Unity before installing CCSM, I have no idea whether I maintained the Unity behavior I was starting to get used to, or have changed things substantially.

At the moment, Unity "feels" different now than before I installed CCSM, but I cannot articulate the differences.

While this experience certainly beats the epic battle against the bloatware packed onto a typical new Windows upgrade, it seems like this upgrade, and I have installed every one since Jaunty, has been fraught with difficulties.

Ubuntu growing pains I suppose, but previous upgrades had been progressively smoother until now. While I was able to dumb my way through previous upgrades, this one required every bit of my pitifully poor command line Kung Fu. If I'd installed Oneiric with the beginner knowledge I had when I started learning Linux under Jaunty, I never would have completed the task.

Be that as it may, Paul, I thank you for your posted solution.

---

### Post by randyklein99 on 2012-03-18
I'm having all these same problems, have tried all the proposed solutions mentioned in this thread and then some, and no luck here.  Unity (3d) is still not working under my account, although the other accounts have no problem.  Unity 2d works just fine though, as does Cinnamon, Gnome3, Gnome Classic, KDE.  I have this identical problem on two PCs (one laptop with Intel HD 3000 graphics and one desktop with Nvidia card). 

I have done a fresh install (but keeping my home directory intact) and the problem persists, so I'm sure the issue is a config file in my home directory.

Any clues?

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-27
This thread is actually about 11.10, and from your post it looks like you are using 12.04 (because you mention Gnome 3)
Did you install CCSM and start to get the problems then?
I'd suggest using a different program to edit Unity like MyUnity
```

sudo apt-get install myunity

```

You may even need to start a new thread about this as this thread is about Oneric (which was based on Gnome 2)  Though it seems to me that a lot of the same things should still be applicable.

CCSM is pretty good a destroying Unity, because you have full control over compiz and how it acts, and Unity has very specific needs within compiz.

So, if you have CCSM, and changed something and then Unity broke, I would suggest purging CCSM
and installing myunity to tweak your system... or go get unsettings
[http://www.florian-diesch.de/software/unsettings/](http://www.florian-diesch.de/software/unsettings/)

---

