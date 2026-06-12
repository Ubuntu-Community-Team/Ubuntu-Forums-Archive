---
title: "How do I stop the display from going to sleep?"
date: 2010-08-11
forum: General Help
---

### Post by disastrophe on 2010-08-11
Hi,
I just recently changed one of my OSs  to Ubuntu 10.04. I have run into a somewhat annoying problem.
Point by point:

The problem: My monitor is going to sleep after 10 min. of inactivity no matter how I have the system set. I do not wish for this to occur, I mean why bother having a screensaver? lol

I am using a desktop PC.

The Power Management daemon is enabled.

I have power management set to - 
Put computer to sleep when inactive for: Never
Put display to sleep when inactive for: Never
When power button is pressed: Shutdown
When suspend button is pressed: Suspend

I have screensaver set to-
Activate screensaver when computer is idle: unchecked
Lock screen when screensaver is active: unchecked
The duration slider is maxed out to 2 hours.

The sleep function of my monitor is turned off.  It's a Compaq WF 1907.
I know it's Ubuntu because my monitor OSD is showing a "No Signal" message when it happens and it never happens when I am using Linux Mint 9. Since LM9 is built on top of Ubuntu, this leads me to believe a setting is simply not taking.

Ubuntu is fully updated.

I have a wonderful desktop set up and I would really hate to scrap it and go back to LM on this partition but this is really irritating. Is there some way to make it work the way it's supposed to?
Any help would be very much appreciated. Thank you.

Machine: HP Pavilion a6319fh w/ Intel G33/35

---

### Post by dnguyen1963 on 2010-08-11
> **disastrophe said:**
> Hi,
I just recently changed one of my OSs  to Ubuntu 10.04. I have run into a somewhat annoying problem.
Point by point:

The problem: My monitor is going to sleep after 10 min. of inactivity no matter how I have the system set. I do not wish for this to occur, I mean why bother having a screensaver? lol

I am using a desktop PC.

The Power Management daemon is enabled.

I have power management set to - 
Put computer to sleep when inactive for: Never
Put display to sleep when inactive for: Never
When power button is pressed: Shutdown
When suspend button is pressed: Suspend

I have screensaver set to-
Activate screensaver when computer is idle: unchecked
Lock screen when screensaver is active: unchecked
The duration slider is maxed out to 2 hours.

The sleep function of my monitor is turned off.  It's a Compaq WF 1907.
I know it's Ubuntu because my monitor OSD is showing a "No Signal" message when it happens and it never happens when I am using Linux Mint 9. Since LM9 is built on top of Ubuntu, this leads me to believe a setting is simply not taking.

Ubuntu is fully updated.

I have a wonderful desktop set up and I would really hate to scrap it and go back to LM on this partition but this is really irritating. Is there some way to make it work the way it's supposed to?
Any help would be very much appreciated. Thank you.

Machine: HP Pavilion a6319fh w/ Intel G33/35

Well, this is an odd problem.  Would you please activate the screen saver and set the duration to 15 min?  Check to see if the computer shuts down after ten minutes or it will stay until the screen saver turns on.  If the screen saver turns on then uncheck the screen saver button and see if the computer still turn off after 10 min.

---

### Post by disastrophe on 2010-08-11
Hmmm, that IS interesting. I turned the screensaver back on, set it for 20 min. - screen didn't blank, screensaver kicked in after 20 min. Afterward I disabled it and everything appears normal. It's been sitting idle for close to an hour and no probs. It would appear to be an issue with the screensaver daemon?(which was set to blank screen.)  I generally don't use screensavers, I was just using that as more of a rhetorical point. 
In any case, it appears that all is well. Thank you very much for the help []("http://ubuntuforums.org/member.php?u=435434")dnguyen1963!

---

### Post by dnguyen1963 on 2010-08-12
> **disastrophe said:**
> Hmmm, that IS interesting. I turned the screensaver back on, set it for 20 min. - screen didn't blank, screensaver kicked in after 20 min. Afterward I disabled it and everything appears normal. It's been sitting idle for close to an hour and no probs. It would appear to be an issue with the screensaver daemon?(which was set to blank screen.)  I generally don't use screensavers, I was just using that as more of a rhetorical point. 
In any case, it appears that all is well. Thank you very much for the help []("http://ubuntuforums.org/member.php?u=435434")dnguyen1963!

No problem!

---

### Post by kevr on 2011-01-13
> **dnguyen1963 said:**
> No problem!

Somewhat unrelated, but your post reminded me about checking the screensaver when I was thinking it was power management display sleep. Thanks :)

---

