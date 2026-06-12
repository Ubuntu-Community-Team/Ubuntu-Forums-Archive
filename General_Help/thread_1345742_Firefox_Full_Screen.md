---
title: "Firefox Full Screen"
date: 2009-12-04
forum: General Help
---

### Post by tienigami on 2009-12-04
As I type this, my firefox is taking up the full screen. Yesterday there was a bar at the bottom that had all my open applications and on the top was the bar that has the time and all that on it. If I'm looking at a different program, like Rhythmbox, the bars are there and stuff, but if I alt-tab to Firefox everything disappears. I feel like this should be an easy fix, but it's really annoying to not be able to fluidly open 'Places' without alt tabbing to a different program.

I tried to reinstall firefox using

'sudo apt-get install mozilla-firefox' 

but it didn't work...

Thanks

---

### Post by ed-koala on 2009-12-04
While Firefox is on your screen, hit F11

---

### Post by Ancanus on 2009-12-04
> **tienigami said:**
> As I type this, my firefox is taking up the full screen. Yesterday there was a bar at the bottom that had all my open applications and on the top was the bar that has the time and all that on it. If I'm looking at a different program, like Rhythmbox, the bars are there and stuff, but if I alt-tab to Firefox everything disappears. I feel like this should be an easy fix, but it's really annoying to not be able to fluidly open 'Places' without alt tabbing to a different program.

I tried to reinstall firefox using

'sudo apt-get install mozilla-firefox' 

but it didn't work...

Thanks

Have you tried pressing F11 while in Firefox?

---

### Post by tienigami on 2009-12-04
Yes, it didn't help. I did more work trying to fix it and the problem is that when firefox first opens up, it is not in maximize mode. It is in loose, window form (more common when it's a small window) that has been stretched to take up too much of the screen. If I am careful I can drag the window down and then resize it, but that modification doesn't stick. Is there any way to make it not open up too big every time?

---

### Post by ed-koala on 2009-12-04
Open your Firefox preferences. Go to Content tab. Go to Enable Javascript - Advanced. Make sure Move or resize existing windows is NOT checked. Resize Firefox to the size you want.

See if that solves your problem.

---

### Post by Ancanus on 2009-12-04
Back-up your profile (~/.mozilla/*.default) and remove it.

See if that solves your problem.

---

### Post by winotree on 2009-12-04
Removing and re-installing Firefox without first deleting the .mozilla file in your /home/user doesn't change anything because all its configuration files are stored there.  Back-up and keep in a separate place a copy of your .mozilla file, then shutdown and restart Firefox.  It will have created a new set of default config files for itself which may fix your problem.

EDIT - Ah.  Someone's already mentioned this.  ;)

---

### Post by ed-koala on 2009-12-04
Try my suggestion before reinstalling.

See this for why - [https://bugs.launchpad.net/firefox/+bug/209499]("https://bugs.launchpad.net/firefox/+bug/209499")

---

### Post by winotree on 2009-12-04
> **ed-koala said:**
> Open your Firefox preferences. Go to Content tab. Go to Enable Javascript - Advanced. Make sure Move or resize existing windows is NOT checked. Resize Firefox to the size you want.

See if that solves your problem.
Now I'd not have thought of that as a solution -- but only because two years ago when I purchased this device I'd changed that option and so that behavior is normal for me.  Completely forgot about it until just now.  Good idea -- would love to hear if it helps.  :)

---

### Post by tienigami on 2009-12-04
You fixed it Ed. Thanks a lot!

---

