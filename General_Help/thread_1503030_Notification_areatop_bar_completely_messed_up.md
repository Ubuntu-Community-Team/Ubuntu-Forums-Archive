---
title: "Notification area/top bar completely messed up"
date: 2010-06-06
forum: General Help
---

### Post by Sandertje on 2010-06-06
Hello,

I've got a very annoying problem with my top bar and the notification area. The icons/applet's order is completely messed up. The icon's overlap, some do not show at all, and sometimes some do not load (seeing a black square instead). Most applet's can also be accesed through Applications or System, but especially the wireless app is necessary to be there. Perhaps there is a way to get to it via another way then the notification area, but then I dont know where :P. The problem isn't consistent; sometimes it's there,   sometime's it's not. Killing the "notification-area-applet" process and then reloading it does sometimes help, but more often than not, a total reboot is all that can fix it. I've attached two pics to illustrate the problem. 

Is there a way to fix this problem? 
Thanks in advance! :D

---

### Post by xpluto on 2010-06-06
same problem here and i get this error too 
>> **_OAFIID:GNOME_FastUserSwitchApplet_**

---

### Post by Sandertje on 2010-06-07
Where do you get that error? As a popup error? I've never experienced any error messages so far. Could there be any useful log file whose content I could post?


EDIT: I have found two bug reports at Launchpad relating to this problem: [https://bugs.launchpad.net/indicator-applet/+bug/439448](https://bugs.launchpad.net/indicator-applet/+bug/439448) and [https://bugs.launchpad.net/indicator-applet/+bug/582162](https://bugs.launchpad.net/indicator-applet/+bug/582162)

---

### Post by bhishan on 2010-06-07
Same problem here.

---

### Post by drs305 on 2010-06-07
For the first post, if you are willing to go back to the straight defaults and lose any customizations you have made to the panel, you can run this command to return to the default settings. It may or may not sort things out for you:
```

gconftool-2 --recursive-unset /apps/panel

```
To refresh the panel:
```
killall gnome-panel
```

---

### Post by itsjustarumour on 2010-06-07
Been getting the same thing on Karmic 9.10 too, for the last 3 weeks or so... icons overlapping, in the wrong order, wrong labels, some shown twice (or one and a half icons).  Somethings gone seriously screwy somewhere in the updates...

---

### Post by Sandertje on 2010-06-08
I just got an update of gnome-panel. I wonder whether this fixes the problem. Only time will tell.

---

### Post by mlejayne on 2010-06-09
I'm having similar issues, and I have updated today.

---

### Post by freakengine on 2010-06-10
I've had similar issues with Gnome in Lucid.  It started with my power icon disappearing, then my chat accounts item was duplicated but the second version was only half as wide, and now the top panel icons are reaaranging themselves into a different order every time I boot.  It's a little bit crazy.  At first I thought it was a screen refresh issue of some sort as making a change in the top panel would often set things right but that no longer works.

---

### Post by fyra on 2010-06-12
My notification area got all jumbled as well. It seemed to be related to plugging into an external monitor with a DVI cable (laptop) and then restarting the computer with it still connected. It picked the wrong resolution for my laptop screen upon restart, and the simple fix is always to unplug and restart again with it unplugged.

When I did though, the notification area was all jumbled and has been ever since.

At about the same time, I noticed that while browsing in Firefox, the computer would take 5-6 seconds after opening a new page, before I can scroll up/down. Later (while typing a forum post) I discovered that it was refusing keyboard input as well, but only for that period. Once the 6ish seconds are up, all the suspended input, be it typing or scrolling, happens in a rush (main thread suspended?).

As to why this is relevant to this thread, I watched the processes tab of system monitor while it happened, and indicator-applet always jumps from being dormant to using 200% of my CPU for this period.

Halp ;)

---

### Post by geofurtado on 2010-07-03
You can move the icons by right-clicking in an area slightly to the side of the icon/s.  Some of them are in groups so you will need to find the correct spot to click on.  A drop-down menu will appear that will permit you uncheck "lock to panel".  After moving things around you can "lock to panel" for each group.

---

### Post by kmisterk on 2011-10-02
> **drs305 said:**
> For the first post, if you are willing to go back to the straight defaults and lose any customizations you have made to the panel, you can run this command to return to the default settings. It may or may not sort things out for you:
```

gconftool-2 --recursive-unset /apps/panel

```
To refresh the panel:
```
killall gnome-panel
```

Perfect! Worked a charm!  I was having an issue where newly created notification icons were being dropped below the far left edge of the top panel. These two things worked perfectly. I won't touch the top bar anymore, but I use a dock as a replacement for the bottom panel

Thanks again!

---

### Post by supershin on 2011-10-22
I'm running Lucid 10.04 and it is up-to-date yet it still sometimes get messed up. The above commands reset it to the defaults but it really is a nuisance to have to run those commands.

---

