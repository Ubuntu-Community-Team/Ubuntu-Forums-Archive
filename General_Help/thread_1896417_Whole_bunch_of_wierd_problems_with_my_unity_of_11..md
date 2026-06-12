---
title: "Whole bunch of wierd problems with my unity of 11.10"
date: 2011-12-16
forum: General Help
---

### Post by huntkey on 2011-12-16
Hi experts,

This is driving my really mad. First it was the ubuntu 11.10 uses a lot CPU. I tried to play around with it with compiz and now Unity crushed. I tried to reset unity and I got many warnings:

```
unity-panel-service: no process found
unity-panel-service: no process found
Initializing unityshell options...done
compiz (core) - Warn: no exact match for ConfigureNotify on 0x1800092!
compiz (core) - Warn: expected the following changes:
compiz (core) - Warn: sibling: 0x43ee95
compiz (core) - Warn: instead got:
compiz (core) - Warn: x: 0
compiz (core) - Warn: y: 0
compiz (core) - Warn: width: 3360
compiz (core) - Warn: height: 1080
compiz (core) - Warn: above: 0
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
DEBUG 2011-12-16 20:26:02 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1920 h=1080
WARN  2011-12-16 20:26:02 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window65011885: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-12-16 20:26:02 glib.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
WARN  2011-12-16 20:26:02 glib.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
WARN  2011-12-16 20:26:02 glib.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
WARN  2011-12-16 20:26:02 glib.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
WARN  2011-12-16 20:26:03 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window65011885: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-12-16 20:26:03 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window65011885: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

...

WARN  2011-12-16 20:26:37 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-12-16 20:26:37 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist

```

Then it stops here. I click on dash home and it can't find anything. I click on any link on it it crashes my entire desktop and I don't see anything on my desktop except a few files I have on my desktop. How can I fix this??

Thanks,

---

### Post by bluexrider on 2011-12-16
**Reset Unity**
*If you want to reset Unity (this will only reset the Unity settings  in CompizConfig Settings Manager and leave the other CCSM settings  intact), open a terminal and enter:*
```
sudo unity --reset
```[B]
Reset Unity Launcher icons[/B]
```
sudo unity --reset-icons
```[B]
Reset Compiz[/B]
```
sudo gconftool-2 --recursive-unset /apps/compiz-1
```

you may want to remove .gnome .gnome2 .gconf .gconfd .metacity .compiz-1 .config/compiz-1 .config/dconf 

then restart

---

### Post by wildmanne39 on 2011-12-16
Hi, try to run unity rest again and just let it run for about three minutes then then reboot and it should be back up if not open compiz and uncheck and recheck unity plugin.

---

### Post by huntkey on 2011-12-17
I have tried all of them. The log in my first post is the output of the "reset" command. Once it reaches the last two lines, it stops. I went for dinner and came back after 2 hours it was still there. I had to Ctrl+Z to stop the process. Once stopped, everything on my desktop disappeared. I rebooted my PC and it came back with the "correct" look. However my "Dash Home" can't find anything. No matter what I search, it displays nothing. I click on any default icon "Media Apps" the unity crashes and everything disappears... Help!

---

### Post by wildmanne39 on 2011-12-17
Hi, I understood that about the log, the unity reset never finishes, it just needs to run about three minutes to get it working again if it is going too.

Did you follow the rest of my suggestions in my last post?

Did you uninstall unity by chance or compiz? 

I have never heard of the dash problem happening once unity is reset so I can not help you with that part.

---

### Post by huntkey on 2011-12-17
Hi wildmanne39 thank you for the replies. 

I just tried to uncheck and check unity. First of all I can't find compiz in the Dash Home. I had to run it through a terminal window Ctrl+Alt+t. I typed in "ccsm" to open the compiz. I unchecked unity and my laucher, task bar, ... all disappeared. Then I checked it again, everything came back up. I clicked "resolve conflict" and disabled something called "flip left plugin". However the Dash Home this doesn't show anything.

Then I did a unity --reset again but this time in the sudo mode (sorry I didn't pay attention and never tied with root user privilege with this command). This time it started to repeat the following messages every 5 mins.

```
(unity-panel-service:6817): Indicator-Datetime-DEBUG: Changing calendar property: calendar-marks
(unity-panel-service:6817): Indicator-Datetime-DEBUG:     Marks: <cleared>

(unity-panel-service:6817): Indicator-Datetime-DEBUG: Changing calendar property: calendar-marks
(unity-panel-service:6817): Indicator-Datetime-DEBUG:     Marks: <cleared>
```

Then I clicked on the Media application button in Dash home I got the following error and it killed the unity reset session. My desktop is gone again...

Did I miss anything?

thanks!

---

### Post by wildmanne39 on 2011-12-17
Hi, the whole desktop is gone? You should have a look at this link it is very good for that problem.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thanks

---

### Post by huntkey on 2011-12-17
Thanks man! that link worked. I actually had to remove all the packages and install them all back based on the link. Now everything looks good. Thanks a bunch!

---

### Post by wildmanne39 on 2011-12-17
Hi, your welcome!!! I am glad it worked.
Enjoy

---

