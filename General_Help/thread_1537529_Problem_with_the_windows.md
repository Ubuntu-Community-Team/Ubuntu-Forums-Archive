---
title: "Problem with the windows"
date: 2010-07-23
forum: General Help
---

### Post by Mago Jose on 2010-07-23
Hello I have a bit of a problem with the windows (not the OS).
the problem is that the last time I actualized my ubuntu the top of my widonws (the bar with the minimize, maximize and close buttons) changed
now is red with the buttons in the right side and I don't know hoy to change it back... I tried getting in the configuration editor -> apps -> metacity -> general -> then in button_layout I change it to close,minimize,maximize:
and it didn't work and the red colour is still there
also when I double click on the bar the window hides under the bar nad I don't know how to make it reapear so how can I change this to just maximize the window (the way it has allways been)
if anyone can solve this it would be very nice
by the way i've trying to find the add-ons i have installed for firefox and i don't know where to find them
they're supoused to be in tools-> add-ons but it doesn't give me that option

if somebody answers thanks a lot

PD: I'm sorry about my english, but i'm not a native speaker

---

### Post by lovinglinux on 2010-07-24
I don't use Gnome, so I don't know the answer to your first problem, but there are [plenty of threads discussing that]("http://www.google.com/search?q=lucid+buttons+right+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0"). 

If Firefox doesn't give you an option to access Tools >> Add-ons, then you might have a corrupted profile. Try to create a new one. You can do that from the Profile Manager.  See these:

[General Troubleshooting Steps](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

[Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by Mago Jose on 2010-07-28
> **lovinglinux said:**
> 
If Firefox doesn't give you an option to access Tools >> Add-ons, then you might have a corrupted profile. Try to create a new one. You can do that from the Profile Manager.  See these:

[General Troubleshooting Steps]("http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html")

[Fixing a problematic or corrupted profile]("http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html")

Hi agian, I tried to fix my firefox profile but i can't. when i type in the terminal

$ firefox -ProfileManager 

just like the link says it just open firefox as usual and doesn't open the profile manager. Any ideas?

I also tryed 

$ firefox -p 

but the same happens

---

### Post by lovinglinux on 2010-07-28
> **Mago Jose said:**
> Hi agian, I tried to fix my firefox profile but i can't. when i type in the terminal

$ firefox -ProfileManager 

just like the link says it just open firefox as usual and doesn't open the profile manager. Any ideas?

I also tryed 

$ firefox -p 

but the same happens

You need to close Firefox first or add **-no-remote** to command.

---

### Post by Mago Jose on 2010-07-29
Thank you for everything, know my mozilla is working just fine

---

### Post by lovinglinux on 2010-07-29
> **Mago Jose said:**
> Thank you for everything, know my mozilla is working just fine

You are welcome.

---

