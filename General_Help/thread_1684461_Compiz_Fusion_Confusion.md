---
title: "Compiz Fusion Confusion"
date: 2011-02-09
forum: General Help
---

### Post by SirCry on 2011-02-09
Hello Unix Users,

I have come into a bad way, I am led to believe this problem is related to compiz fusion hence the title. 

The tops of my windows (with the exception of Chrome) had disappeared, the 'bar' if you will, had gone and vanished. This had happened before Maverick and seemed to resolve itself after an update or something other change to the system.

This time I was curious and looked up the potential cause for it, on these forums no less, and the answer came that it was a "glitch in something Compiz-related"; It was said that the fix was to be found in some "advanced settings" that I couldn't find. Since I hadn't been getting much out of Compiz Fusion (except frustration) anyway I decided to just uninstall it. Simple as that.

Though upon uninstall I decided to reboot (out of habit I guess) and lo! but not only were the windows still bar-less, my multiple work-spaces disappeared, and the sticky notes I had posted all about my main space were persistently stuck there, they could be moved, but even enabling the "hide sticky-notes" option seemed to have no effect. The windows didn't seem to appear atop the notes alt-F4 didn't close the pages (only right-clicking and selecting "close" did) and selecting what I believe to be Back-ups of my distro at GRUB-page seemed to be exactly where I left off, disappointed. 

Help me please.

---

### Post by SirCry on 2011-02-17
It seems the problem is just so easy to fix, I did what Compiz wouldn't allow me to do during it's reign; I went to "extra" effects under appearance, after an update (the update itself didn't seem to change anything, though.

---

### Post by dh04000 on 2011-02-17
Install compiz fusion icon. (Use synaptic to find)

Use it to reload compiz when the crash your describing happens.

Works for me.

---

### Post by Chronon on 2011-02-17
You can also use it to switch between Compiz and Metacity.  I find it to be an essential piece of software if you're going to run Compiz.

---

### Post by pqwoerituytrueiwoq on 2011-02-17
> **dh04000 said:**
> Install compiz fusion icon. (Use synaptic to find)

Use it to reload compiz when the crash your describing happens.

Works for me.
if you select compiz under "select window managers" i think it reloads faster but it takes longer to get to than the strait reload
@[Chronon]("http://ubuntuforums.org/member.php?u=415106")
i think putting this on a keyboard shortcut is more convienent
```
cat /opt/toggle-Metacity-and-Compiz.sh
#!/bin/bash
if [ 0`pidof metacity` -gt 0 ]; then
    compiz --replace
else
    metacity --replace
fi
exit
```

---

### Post by SirCry on 2011-02-21
Thank you all, 

I've decided to just go without Compiz, I believe there are some conflicts with my Graphics card (which manifest as a blue play-back on videos as well). The biggest problem seems to be with the "visual effects" of this all, which don't seem to stay as I set them post-reboot. It's when I set the effects from (none) to (extra) that the lack of "top bars" on windows seem to fix itself. 

I just have to do this every time I reboot, it's bothersome.

---

### Post by stinkeye on 2011-02-21
When you set the the visual effects to normal or extra you are changing to
compiz as your window manager.
If set to none you are using metacity as your window manager.

Metacity draws the window plus titlebar and border

while

compiz only draws the window and needs **emerald** or **gtk-window-decorator**
to draw the titlebar and borders.


If your running compiz
alt+F2 and run 
```
gtk-window-decorator --replace
```
should make the titlebar and border appear.

This should all happen automatically and you've probably just got some botched compiz settings which can easily be fixed.

---

