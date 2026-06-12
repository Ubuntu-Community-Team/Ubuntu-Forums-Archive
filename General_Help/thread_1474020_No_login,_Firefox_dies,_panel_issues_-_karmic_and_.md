---
title: "No login, Firefox dies, panel issues - karmic and lucid"
date: 2010-05-05
forum: General Help
---

### Post by def_mornahan on 2010-05-05
I've been having very weird issues for the past couple of days, and have looked through the forums and web and tried everything I can think of to fix it.

I was minding my own business running Karmic on an old Dell Dimension 8200 with my little 14.1" flat panel monitor when I rebooted and found that I no longer got the graphical login prompt, although the Ubuntu logo had shown up, the spinner progress bar had been running, and I was still looking at the spotlight splash screen background (i.e. not a black screen).  The system was completely unresponsive to the keyboard, and although the mouse pointer was visible it had no effect on anything.

I tried uninstalling and reinstalling gdm from the console, but that didn't work.  I found I could get to Gnome by uninstalling gdm, selecting the console prompt from the "low graphics mode" dialog box that came up, and then using startx, but there were other weird things that happened.  I got a bunch of dialogs saying that the notification area applets wouldn't work, and did I want to remove them from startup (foolishly I said yes).  I also found that if I try to Add to Panel, the panels just disappear then reappear and I get no dialog box.  If I try to invoke Firefox, the window flickers into being for a moment then disappears; the pointer stays on wait mode for a little longer, then nothing.  Other applications all open just fine, but I can't access them from the bottom panel (i.e. where they go when minimized).  I have to use Alt-Tab to get at minimized windows.

The last thing I remember doing that could conceivably have affected the display settings was installing wxWidgets by hand, to attempt to run a piece of scientific software, but that was last week and I'm pretty sure that I restarted at least once since then without problems.

I checked the memory and hard drive and these seem to be fine.  The hard drive is prob. the newest component to the system but I think it's from 2005/6.

Meanwhile, I've reinstalled 9.10, tried the proprietary nvidia drivers for my GeForce 6600 card, swapped out graphics cards to an old GeForce 200, and installed 10.04.  I haven't reformatted my / partition, but have been writing over the old installations, i.e. not side by side.  (I backed up my documents, but haven't done my music and pictures.)  The problems persist.  Also, Ubuntu cannot identify my crappy old monitor and currently, under Lucid, claims I'm running a Gold Rain Enterprises Corp. 18" (the back of my monitor says 14.1" TFT LCD Monitor, Model MO-141; I believe when I ordered it from Newegg circa 2004 the brand name was Allystar).

Is it worth wiping the hard drive and doing a completely clean reinstall?  What gives?

---

