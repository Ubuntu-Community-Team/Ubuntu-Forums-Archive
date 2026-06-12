---
title: "&quot;Put Display to Sleep&quot; works only once"
date: 2010-06-09
forum: General Help
---

### Post by Randypan on 2010-06-09
Hi everyone,

I 'm using Jaunty on a HP530 laptop. I've disabled the screen saver and set the time until idle to 29 minutes. In the Power management window, I have set the display to go to sleep after 30 minutes of idle state. _This setup worked like a charm from the beginning untill three or four days ago_. From then on, after every reboot display sleep only works for the first time in every session and then the sreen just stays on untill I turn the computer off. The only major changes in my system coinciding with when I first noticed this irregular behaviour are the latest automatic updates I got and an accidental transition to 'Suspend' mode. I 've never tried Suspend before in my computer and though I met no difficulties with the process I've heard that in some cases 'Suspend' may interfere with power management. 
The only course of action I have taken towards solving the problem is replacing my /etc directory with one backed-up before the problem showed up -in case something was changed in there- but the problem persists.
Anyone have any ideas?

If there's any useful info regarding my system I might have forgotten to mention please point it out.

---

### Post by Randypan on 2010-06-10
Another thing I recall having done shortly before noticing this problem is ticking the entry that says "Do not prevent screensaver from operating when playing audio files" in the Totem's Settings window. I eventually unticked it but nothing changed. 
To be honest I don't even know if the faulty behaviour began at the point of time i mentioned in my above post. It might have been there all along and I just happened to notice it recently.
I'm baffled here guys. Is there anyone around here facing or having faced the same issue that might provide some info?

---

### Post by Randypan on 2010-06-12
Update: I went a little rabid and tried everything all at once. I uninstalled gnome-screensaver, installed xscreesaver, uninstalled it because it wouldn't cooperate with gnome power manager, reinstalled gnome screensaver, and activated xset dpms which wasn't such an elegant solution as it wouldn't take media players into account and blanked the screen while I was watching a movie.
  The only thing that has changed in my system setup now is dpms ( before it was set as "off", now it shows up as "on" with zero values for "sleep", "suspend" and "monitor off"- so it's as good as off).
  After all this mess I set off-time in power management to 2 mins and it worked. I then increaced it to 30 mins and it seemed to be working too. The screen turned off three times in a single session. During that session only the file manager, VLC, Transmission and Firefox were used. After that and before going to bed I played an audio CD with Alsaplayer, left the computer on _and the next morning the monitor was on_.  GAAAAHHH! Somebody please tell me what's wrong...

---

### Post by Randypan on 2010-06-13
I found out that although I had the latest kernel version downloaded i still used .16, so I updated menu.ist to boot into the .19 kernel. I hoped this would make a difference but monitor sleep still works in strange ways. By fiddling with different idle times I came to conclude that monitor sleep works fine for some amount of time (a few hours) and if i'ts woken up after that time has passed, it never goes to sleep again. 
I also searched around the forum and found similar cases of malfunctioning power management affecting mainly Lucid. In none of these tnreads was the issue resolved or even discussed. 
I can't understand, is this issue Taboo in any way? Surely, there must be someone out here who can at least vaguely point to the correct direction towards a workaround. 

Please, need help here. I'm waking up every morning only to find my monitor on after hours of non stop operation.

---

### Post by Randypan on 2010-06-13
anybody?

---

### Post by Randypan on 2010-06-18
I found the solution thanks to this walkthrough [http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html). I modified my xorg.conf file and now my computer goes to sleep every 30 minutes without any trouble.

---

