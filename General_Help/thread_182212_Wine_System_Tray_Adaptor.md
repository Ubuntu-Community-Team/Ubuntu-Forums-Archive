---
title: "Wine System Tray Adaptor"
date: 2006-05-25
forum: General Help
---

### Post by groggyboy on 2006-05-25
I just installed and set up uTorrent on my computer using wine.

When I run it, a little uTorrent icon appears in its own little window in the top left corner of my screen.  The window's name appears as Wine System Tray Adaptor in the Window List.  I presume this icon is supposed to appear in the Notification Area?

Why isn't it appearing there automatically, and how do I make it appear there?

groggyboy

---

### Post by evilgold on 2006-05-25
Okay, i know this doesnt answer your question but, have you tried ktorrent? I've found its the closeset thing to utorrent on linux. You might want to give it a look.

As for your question, I havnt used wine in a while but i think the wine tray is supposed to be seperated from the notification area.

---

### Post by citizenr on 2006-07-01
I have the same problem, just installed uTorrent and want to integrate Wine tray with Gnome tray
icame here from google, guess its back to google then :/

EDIT:

lookie what I found in google :
[http://www.winehq.com/pipermail/wine-users/2004-July/014382.html](http://www.winehq.com/pipermail/wine-users/2004-July/014382.html)
------------------------------------------------------------------
On Wed, 07 Jul 2004 10:46:02 +0100, you wrote:

> On Sun, 04 Jul 2004 19:19:11 +0200, Rein Klazes wrote:
> > As a work around you can uncheck the "Place an icon on the windows 
> > system tray" option (tools/options/user interface).
> 
> If the app is deadlocking due to the system tray icon, applying my 
> systray patch may work as well.
> 
> thanks -mike

With the patch an icon appears in gnome's notification area and you can
restore a responsive Pegasus from there :-)

What is not so nice:
- You can restore the Pegasus window, but the horizontal size is wrong (far
too small);
- The Pegasus icon still appears on the task bar (and is unusable);
- Also when you change desktops, Pegasus re-appears unresponsive. Also here
the notification area can be used to get a working window.

------------------------------------------------------------------

so it is an OLD wine bug known from at least Jul 2004 :(. Everything including wrong horizontal size and empty window after clicking on taskbar is the same. There is a patch for tray to gnome notification area thing somewhere, will keep diggin.

---

### Post by pmagill on 2006-07-13
Hi same problem its not just wine, happens with amarok, Katapult and others, not a program error but a Gnome one I would assume.....although my mail notifier happily sits there?

Does anyone have a clue, I miss being able to hide amarok in the corner...and it makes Katapult redundant..

Pat

---

### Post by ba5e on 2006-08-16
you can get any wine system tray icon to go into the gnome system tray by loading a KDE app with a system tray icon first.

I like Amarok so I use that:

```
sudo apt-get install amarok
```

you might need to change your repositories before that works.

Another tip is to set Amarok to open in the tray at start up. Do this in system, preferences, sessions, startup programs. Just add Amarok.

Now whenever you open uTorrent it will go to the tray.

---

### Post by Giggity on 2006-08-21
Neat trick... now to find out how to bypass loading amaroK and just go straight to the GNOME native system tray.  Thanks.

---

### Post by komputes on 2007-12-23
I got a Wine System Tray Adaptor through Picasa (for linux not windows) window as well, couldn't find the process name to kill it. Had to reboot. does any know the name of the process?

---

### Post by Magnentius on 2008-04-28
The amarok workaround worked fine with me but that changed since Ubuntu 8.04 with Wine 0.9.60 (from WineHQ.org). Now their appears a large window containing the systray icon and the same icon appears often next to the amarok one too. Does anyone know how this is caused?

---

### Post by Magnentius on 2008-05-04
I think the silence on this forum is a sign of a bug. So I reported it: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/226494](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/226494)

---

### Post by bullet.proof on 2008-07-13
The bug is marked as "fix released".

But I have a similar problem. I'm using Proxomitron (Naoko 4.51) on Wine 1.1.1. It works great in Ubuntu 8.04. The icon appears where it should appear - when starting manually over panel.

BUT when I start Proxomitron at system startup (using Settings -> Sessions), this annoying Wine System Tray appears, and the icon is in there, not in gnome system tray.

Is there any solution?

---

