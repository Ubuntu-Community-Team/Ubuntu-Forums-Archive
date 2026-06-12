---
title: "netbook-launcher and ubuntu-desktop"
date: 2010-05-17
forum: General Help
---

### Post by Ampi on 2010-05-17
For some reason, the last two times I booted my netbook (I just installed UNE 10.04) my ubuntu-desktop is back on it without the netbook-launcher. 

From the terminal I tried to install the netbook-launcher, but it tells me I already have it.
From the terminal I tried to remove the ubuntu-desktop, but it tells me I do not have it installed.
I also tried to install the desktop-switcher (with terminal and synaptic) but the package doesn't exist or hasn't been found.

How can I get the netbook-launcher visible again? I really like it and I only have an 8"9 screen... :(

---

### Post by kerry_s on 2010-05-17
just put "netbook-launcher" in your startup.

---

### Post by Ampi on 2010-05-18
You mean the startup apps?? What would be the command for that?

---

### Post by Ampi on 2010-05-24
bump..

---

### Post by kerry_s on 2010-05-24
> **Ampi said:**
> You mean the startup apps?? What would be the command for that?

**netbook-launcher**

---

### Post by Ampi on 2010-05-26
I added it to my startup apps but it doesn't work. Are you sure that just netbook-launcher works as the command? Shouldn't be an entire path?

---

### Post by kerry_s on 2010-05-26
> **Ampi said:**
> I added it to my startup apps but it doesn't work. Are you sure that just netbook-launcher works as the command? Shouldn't be an entire path?

yeap, i'm sure. sure you can use the entire path if you want, in a terminal type:
**whereis netbook-launcher**
& it will show you the path.

what happens when you run "**netbook-launcher**" from terminal?

i use the lite version on mine, on openbox with xfce4-panel. my startup is a file.

---

### Post by kerry_s on 2010-05-26
try logging out & checking the session menu for netbook.

---

### Post by Ampi on 2010-05-27
Now I see, there is some kind of a problem.. This is my output when I type in netbook-launcher, if I ask whereis, I just get three normal paths..
I'm gonna try the logging out in a bit, but I guess the terminal output says there is something going on.. 
Any idea?

P.S. It is pretty much a new install..

```
netbook-launcher: /usr/bin/netbook-launcher /usr/share/netbook-launcher /usr/share/man/man1/netbook-launcher.1.gz
amparo@amparo-laptop:~$ netbook-launcher
** (process:2521): DEBUG: OpenGL renderer string: Mesa DRI Intel(R) 945GME GEM 20091221 2009Q4 x86/MMX/SSE2

(netbook-launcher:2521): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:2521): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:2521): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:2521): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:2521): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Ubuntu Software Center
(netbook-launcher:2521): liblauncher-DEBUG: Workarea: (0, 24) (0, 0)
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
** (netbook-launcher:2521): DEBUG: Not loading modules: Error opening directory '/usr/lib/netbook-launcher/plugins': No such file or directory

(netbook-launcher:2521): Clutter-WARNING **: The actor 'NlSidebarScrollbutton' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'CtkVBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'CtkHBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'CtkToplevel' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'CtkScrollView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'NlSidebarScrollbutton' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
Application Created: Netbook Launcher Netbook Launcher
Application Matched: Terminal Terminal
Application Matched: Chromium Web Browser chromium-browser
Application Created: File Manager File Manager
Application Created: Top Expanded Edge Panel Top Expanded Edge Panel

** (netbook-launcher:2521): WARNING **: Unable to find FavoritesLoader for ubuntuone-client-applet, type (null)

(netbook-launcher:2521): Clutter-WARNING **: The actor 'NlScrollView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'NlContentView' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'CtkHBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(netbook-launcher:2521): Clutter-WARNING **: The actor 'CtkToplevel' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
^C** (netbook-launcher:2521): DEBUG: Signal caught: 2
** (netbook-launcher:2521): DEBUG: Quitting nicely

(netbook-launcher:2521): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

### Post by Ampi on 2010-05-27
I just logged out, and logged in as me with the session, Netbook Edition 2D. At first I see the Netbook desktop, but once completely loaded it appears as the 'normal' Desktop Edition...
But I guess this was predictable after the terminal output..

---

### Post by kerry_s on 2010-05-27
has it ever worked on your machine before?

when i use the normal "netbook-launcher" it locks up my computer, but the lite version works fine, so i guess there just a bit picky on what they work on.

mine is also intel graphics by the way. i also turn of the effects as that locks up for no reason to.

i decided to just ditch it for now, i'm just using the standard gnome, did a fresh install about a hour ago.

:( hopefully some day they'll just work. :)

---

### Post by Ampi on 2010-05-27
For me it has never been a problem. I ve had UNR 9.04 and 9.10 end when 10.04 came out I installed it perfectly fine. 
But I forgot to make partitions so I reinstalled it, and it worked until the first time I rebooted...
I might reinstall it also, got my partitions now anyway... But it is weird..
Maybe someone reads this message before  actually reinstall.

Too bad, you can't use it, it does help me with the small screen.. :(

---

### Post by kerry_s on 2010-05-27
not really a problem for me, i'm using a nettop with a 14' lcd 1024x768, anyways there ton's of options to get screen space if needed, i did a openbox + xcompmgr + cairo-dock that just gives you the whole screen, in fact i was just thinking abut doing it with gnome this time.

---

### Post by Ampi on 2010-05-28
Yes, that's true, but I like the easy switching between applications and the little space on the panel for open applications. But it's just that I know it can work, I'll probably   try to reinstall the launcher, if not  I'll do a complete reinstall, but now Im to lazy to do this :)

---

### Post by dleonov on 2010-07-16
Commenting out the following lines in /etc/X11/xorg.conf helped me with  the similar problem:

Section "DRI"
            Mode    0666
EndSection

(BTW: I have 2 netbooks and I had the problem only on Eee 1101HA with poulsbo video adapter)

---

### Post by kerry_s on 2010-07-16
there's no xorg.conf on a default install, you need to make that.

i have mine fully working now after the last kernel update.
i replaced gnome-panel with awn + xcompmgr, cleaned up the launcher a bit. awn is set below, pops up when i move the mouse to the bottom. i turned off undecorate in maximus.

---

### Post by Ampi on 2010-07-22
Thanks, this sounds very promising, I´ll try it in the morning and let you know how it went :)

---

### Post by Ampi on 2010-09-09
It will probably have no point trying any longer to fix this as we're getting close to 10.10, but still. The problem might just continue with the new one..
I reinstalled my netbook, I see the launcher for a couple of seconds and then it just disappears. I never had this problem before I started this thread. 

After a bit more of thinking I came up with the following question: Does the netbook launcher save anything in my home folder? 

Because I do have two partitions (/ and /home) where /home is the only one not being formatted. Everytime I reformat or reinstall I am surprised by the many settings that aren't lost, like WiFi passwords. Maybe a complete reinstall will do the trick, though I wouldn't want to loose all the passwords..

---

