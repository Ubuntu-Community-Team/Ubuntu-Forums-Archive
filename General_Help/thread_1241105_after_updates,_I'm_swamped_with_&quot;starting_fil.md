---
title: "after updates, I'm swamped with &quot;starting file manager&quot; whenever I boot"
date: 2009-08-15
forum: General Help
---

### Post by MaxIBoy on 2009-08-15
UPDATE: This problem has been fixed. If you arrive at this page because you have the same problem, I suggest checking the order of your initscripts, as that solved it for me.




==========[original post]===================

I updated about 250 different packages yesterday and removed a few as well, now whenever I boot up I get swamped with "starting file manager" listed in the window switcher, with perhaps four new ones added per second. The first screenshot is what it looks like at first boot up.

Then, it's the darndest thing... after a few minutes *my theme dissappears!* This is what it looks like now (second screenshot.)


I'm using Ubuntu 9.10 (and if you're just going to say "serves you right for using an alpha test," please don't say anything at all.) Has anyone encountered anything like this before, and if so, how was it fixed? My GNOME session hasn't been mangled in any way, it's the same as it was before when everything was working.

The computer seems to be working okay, but my window switcher is clogged up and that's annoying. 


*time passes*

Since I typed that, my computer got truly wedged twice, so I needed to give it a few minutes to pass. The gunk in my window switcher seemed to subside significantly, then come back with a vengeance. Currently, they're all gone, but it's been exactly 24 minutes since I booted the computer, I can't go through this every time I boot. 


Sorry if this problem seems so weird, that would be because it *is*.

---

### Post by michy99 on 2009-08-15
Try this:

Make sure every thing is closed out.

Go to System->Sessions->Startup Applications.

Under the Options tab make sure that 'Automatically remember...' IS CHECKED.

Log out and back in.

Nothing should start up this time. Go back and UNCHECK 'Automatically remember...'

---

### Post by MaxIBoy on 2009-08-15
Nope, same result. 

This time I left for an hour or so so it would clear itself up. It got so bad that I had to switch to a virtual terminal and run "killall nautilus."

Only when I switched back, I got a black screen with one of those swirly "the computer is currently choking" mouse cursors. I left it like that for twenty minutes and it didn't change, so I hard-reset.

However, my fluxbox session is working without a hitch, albiet only on one monitor, so that's what I'm using right now. 


Any other ideas?

---

### Post by MaxIBoy on 2009-08-15
Okay, I fixed it!


On a hunch, I checked the order of my initscripts in /etc/rc2.d. It turns out that they'd somehow gotten rearranged such that GDM was being run before almost everything else. I moved GDM to the end where it should be, and checked by rebooting.

Problem officially solved!

---

### Post by airbuzzer on 2009-08-27
How did you manage doing? I just clicked logoff and a dialog comes up telling me to close something, all the file managers close out and then I just hit cancel and everything works like normal.

---

