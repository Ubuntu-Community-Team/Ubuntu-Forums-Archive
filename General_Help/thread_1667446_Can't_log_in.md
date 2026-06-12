---
title: "Can't log in"
date: 2011-01-14
forum: General Help
---

### Post by aflyingturtle on 2011-01-14
So I was trying to repartion the size of the ubuntu portion so I made a live cd with Gpart on it. I ran the cd, and for whatever weird reason, When I ran the gpart, It would start, run for a while and say it was searching for partions for about 10 secs, then promptly close. Now, when I try and run normal ubuntu without the live cd in, It won't let me login and says that Gnome Power Manager's configuration defaults weren't installed correctly. It actually lets me login, but then It just goes straight back into the login menu. As a last thing, My theme got switched to something Weird. I have no idea what happened. I did however boot linux and safemode and succesfully logged in through the command line. So i'm primarily looking for a command line way to get the default config files for Gnome Power.

---

### Post by quixote on 2011-01-15
Hmm.  No real idea what's wrong.  One guess: the liveCD with GParted was corrupted in some way, and that's left garbage on your system.  I'd be very surprised if it was only Gnome Power Manager having problems.  That's probably just the first error message the system brings up.  I'd try another liveCD, ideally one of the stock ones from Ubuntu (they have gparted on them), and try running gparted again.  Maybe it'll be able to fix the problems it created.

Given that you can boot to ubuntu recovery mode, there's another thing to try:  Attach an ethernet cable, boot into recovery mode.  Select the option for "root with networking" (something like that, don't remember the exact wording).  Then, when you have the # prompt, type```
dpkg --configure -a
```That's supposed to fix broken packages.  Don't make any typos because you're root at this point, and can do anything, up to and including destroying your system.

After it's done and you have the command prompt again, type "reboot" or "halt" (without quotes) to restart or stop the system.

---

