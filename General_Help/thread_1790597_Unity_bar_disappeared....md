---
title: "Unity bar disappeared..."
date: 2011-06-25
forum: General Help
---

### Post by nash black on 2011-06-25
My unity toolbar has disappeared. The old style ubuntu panels have appeared in its place. This was happening on occasion before, but restarting the computer would get rid of it. This time unity has been gone for about a week, through many reboots, driver re-installations, etc.

I just installed a new graphics card, which is working fine on the windows partition. Unity would fail to load on occasion with the old card, too. I know the new card works with Ubuntu, because Unity was working fine with it for about a week.

I'm running Ubuntu 11.04. The old card was a GeForce 7900 GT, the new one is a low-profile Sparkle GeForce 8400 GS.

Whats goin on here? I was just starting to get used to Unity!

Thanks

---

### Post by nash black on 2011-08-03
Been more than a month of updates and still no unity. Are these nVidia driver problems going to stick around?

---

### Post by nash black on 2011-08-20
Okay, now unity shows up and works perfectly in the login accounts I made for my mom and brother, but not in mine...

Why would this be and how could I fix it?

---

### Post by uRock on 2011-08-20
Are you logging in with Ubuntu Classic? Can you take a screenshot?

---

### Post by nash black on 2011-08-20
Here is the desktop SS


[IMG]http://imageshack.us/photo/my-images/823/screenshotjx.png/[/IMG]

---

### Post by nash black on 2011-08-20
eh, here is the desktop SS link

[http://img823.imageshack.us/img823/1033/screenshotjx.png](http://img823.imageshack.us/img823/1033/screenshotjx.png)

---

### Post by nash black on 2011-08-21
Also, there is no mode drop down menu (where you could select classic, etc)on the start-up screen. It just isn't there.

---

### Post by dino99 on 2011-08-21
open a terminal and run:

unity --replace &

---

### Post by madhater on 2011-08-21
Alternately you could run unity ---reset-icons

- madhater

---

### Post by nash black on 2011-08-21
Progress! but not quite there... Both commands do appear to do the same thing. They load untity until I log off or restart. When I log in again, Unity is gone. Here is the result of the command (the first one)

```
 tristan@Computus:~$ sudo unity --replace &
[1] 1770
tristan@Computus:~$ unity --replace &
[2] 1771

[1]+  Stopped                 sudo unity --replace
tristan@Computus:~$ unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
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
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:1774): DEBUG: Unity accessibility initialization
** (<unknown>:1774): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x1024

unity-panel-service: no process found
** (<unknown>:1774): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:1774): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:1774): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1774): DEBUG: PlaceEntry: Applications
** (<unknown>:1774): DEBUG: PlaceEntry: Commands
** (<unknown>:1774): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:1774): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:1774): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=1024
** (<unknown>:1774): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
** (<unknown>:1774): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:1774): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:1774): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1774): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1774): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1774): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1774): DEBUG: IndicatorAdded: libme.so
tristan@Computus:~$ ** (<unknown>:1774): DEBUG: IndicatorAdded: libsession.so
 
```


Also, Unity used to disable my pannel at the bottom of the screen. These commands do not seem to do this. It is still there... That is no big deal, it just makes me wonder if something isn't being completely loaded...

---

### Post by nash black on 2011-08-21
Ah its booting and logging in with Unity now.

Thanks!

---

