---
title: "monitor powers off during film"
date: 2009-09-12
forum: General Help
---

### Post by SlugSlug on 2009-09-12
my monitor powers off during watching a film - around 20mins  

system > preferences >  power = 1hour 
screensaver =  2hours

what can I do?

---

### Post by mike555 on 2009-09-12
set your screensaver time...

== opp's reread it , guess you already did that ..  have you tried logging off and back on? ==

---

### Post by paradigm2 on 2009-09-12
Check your BIOS for any strange power settings.  Some older hardware has this.

---

### Post by SlugSlug on 2009-09-12
its not BIOS 

card is Nvidia, but had a look round settings and nothing there either

---

### Post by SlugSlug on 2009-09-19
this is getting really annoying, it's 20 mins into a film then monitor goes off - - where can I look for settings ?

---

### Post by harry_i_c on 2009-09-19
Can I ask what program you are using to watch the films?

---

### Post by NoaHall on 2009-09-19
gksudo gconf-editor

apps ->  gnome-screensaver

see what's going on there.

---

### Post by SlugSlug on 2009-09-19
> **NoaHall said:**
> gksudo gconf-editor

apps ->  gnome-screensaver

see what's going on there.



(am using totem)


cheers NoaHall  in here I have a bunch of stuff - - none says 20mins... 

I've included a screen shot...

---

### Post by NoaHall on 2009-09-19
Untick idle delay activation, or change it to 30 mins, see if it works.

---

### Post by SlugSlug on 2009-09-19
thanks, I've set it to 120 -- -- I'll post back next time I watch a film...

---

### Post by Blakefreak on 2009-09-19
I have the same problem...  Very annoying.

I've tried every setting I can find and nothing helps

---

### Post by SlugSlug on 2009-09-20
This is still a problem.... :( 


any other ideas?

---

### Post by SuperSonic4 on 2009-09-20
I know VLC disables the screensaver but no idea in totem

---

### Post by SlugSlug on 2009-09-20
it used to... it must be something I've installed thats changed something somewhere :confused:

---

### Post by SlugSlug on 2009-10-05
can anyone else help on this - it seems to be after 25mins the monitor goes off..

---

### Post by cynicalcylon on 2009-10-08
I'm having exactly the same problem.

I've reset every preference I can find to do with screensaving/powering down, but it always seems to reset itself to powering down the monitor after about 20-30 minutes.

HELP!

---

### Post by cynicalcylon on 2009-10-08
> **NoaHall said:**
> gksudo gconf-editor

apps ->  gnome-screensaver

see what's going on there.

I've given this one a try myself, so will post back if it does (or doesn't **shrug**) do the trick.

---

### Post by brukutu on 2009-10-08
set this on ur .xsession file

setterm -blank 0 -powersave off -powerdown 0
xset s noblank
xset -dpms
xset s off

---

### Post by mechro on 2009-10-08
Edit::redface::redface:

---

### Post by cynicalcylon on 2009-10-09
> Originally Posted by **NoaHall**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7976546#post7976546")                 
                 [I]gksudo gconf-editor

apps ->  gnome-screensaver

see what's going on there.[/I] Well, this one didn't work.
I set it to 240, but the screen still went off after about 30 minutes.


> **brukutu said:**
> set this on ur .xsession file

setterm -blank 0 -powersave off -powerdown 0
xset s noblank
xset -dpms
xset s off

Where would I find the .xsession file?

---

