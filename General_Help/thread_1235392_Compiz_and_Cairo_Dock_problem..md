---
title: "Compiz and Cairo Dock problem."
date: 2009-08-09
forum: General Help
---

### Post by toejamfootball on 2009-08-09
I have installed Compiz, but when I run compiz --replace in the terminal I get this

```
james@james-desktop1:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1600x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 


```

And it just hangs, sometimes it has an extra line at the end "Starting gtk-window-decorator" and it also just hangs after that.

The Cario Dock looks fine at this stage, but If I close the terminal and reboot it goes back to having just a shitty black background.

Any help is greatly appreciated. Thanks!

---

### Post by gradinaruvasile on 2009-08-09
Install fusion-icon. That will help you launch Compiz/switch between compiz and metacity, launch the compiz settings manager etc. VERY handy stuff. Should be installed by default.

install it by typing:

sudo apt-get install fusion-icon

in a terminal

Oh and cairo-dock has black background because a compositing manager (compiz or metacity's own compositing manager) isnt running.

---

### Post by P4man on 2009-08-09
if you launch something from the console, the process remains attached to it.. so if you close the terminal window, you also end that process (/app). In your case, you close Compiz again.

For instance, try running gcalctool from a terminal. Then close the terminal, the calculator will close as well.

You can avoid that by launching it like this:
```
gcalctool **&disown**
```

Now you can close the terminal and calc will continue running. The terminal no longer "owns" the process.

Similarly, you could launch compiz like:

```
compiz --replace &disown
```

All that said, gradinaruvasile's solution is probably easier :)

---

### Post by toejamfootball on 2009-08-09
> **gradinaruvasile said:**
> Install fusion-icon. That will help you launch Compiz/switch between compiz and metacity, launch the compiz settings manager etc. VERY handy stuff. Should be installed by default.

install it by typing:

sudo apt-get install fusion-icon

in a terminal

Oh and cairo-dock has black background because a compositing manager (compiz or metacity's own compositing manager) isnt running.

Cheers, I installed that, but it still doesn't get any further than xgl not present.

> **P4man said:**
> if you launch something from the console, the process remains attached to it.. so if you close the terminal window, you also end that process (/app). In your case, you close Compiz again.

For instance, try running gcalctool from a terminal. Then close the terminal, the calculator will close as well.

You can avoid that by launching it like this:
```
gcalctool **&disown**
```

Now you can close the terminal and calc will continue running. The terminal no longer "owns" the process.

Similarly, you could launch compiz like:

```
compiz --replace &disown
```

All that said, gradinaruvasile's solution is probably easier :)

Thanks man, I did figure this one out today also :)

---

### Post by P4man on 2009-08-09
Not sure if your problem is solved now or not, but "xgl not present." doesn't mean there is a problem. You don't need xgl for compiz to work on nvidia cards. 

If you run any app from the terminal window, all the output goes in to the terminal window and linux apps tend to be quite verbose throwing tons of errors and warnings and other info. No need to worry about it if it works :)

---

### Post by toejamfootball on 2009-08-09
> **P4man said:**
> Not sure if your problem is solved now or not, but "xgl not present." doesn't mean there is a problem. You don't need xgl for compiz to work on nvidia cards. 

If you run any app from the terminal window, all the output goes in to the terminal window and linux apps tend to be quite verbose throwing tons of errors and warnings and other info. No need to worry about it if it works :)
The thing is it was only working until I shutdown or logged out.

Somehow it is working now though. I will leave the thread not solved for a couple more days just incase :)

---

