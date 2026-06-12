---
title: "cant access files, no application button"
date: 2009-11-05
forum: General Help
---

### Post by badgethefarmer on 2009-11-05
ok.. here it goes.

it's been a while since i had a major problem w/ xubuntu.

first, i couldnt access my files with thunar because thunar keeps on crashing on me. i decided to remove it using synaptic and tried out gnome-commender and pcmanfm via add/remove. after this is done, both newly installed file manager showed the same behavior. after a little rebooting of this machine, the 'applications' button on the top panel just disappered. now, i am launching programs using the terminal.

i really dont know what happened. what i'd like to do is to back up my important files right now and make a clean install of the karmic asap. 

any help from the experts is highly appreciated.

thank you.

---

### Post by P4man on 2009-11-05
I dont know xfce (xubuntu) but in gnome you would just right click the panel, add to panel and select the main menu and/or the menu bar. I suspect its similiar in xubuntu?

---

### Post by badgethefarmer on 2009-11-06
BUMP!

i have not resolved the problem yet. the solution you said regarding right-clicking toolbar did not work. 

i installed thunar again. opened through terminal then the freezing happens again. 

i am pretty sure i did not do anything to make it behave like that. 

web surfing seems good and nothing changed. applications in general are well working.

i thought if there was something wrong with my internal HD so i booted up a live CD of jaunty xubuntu. well, it didnt froze at all but i thought, i cant tell whether the the HD is working fine from booting up a live .iso

i am using a diff machine now to type this. 

i am not giving up on this :D

---

### Post by P4man on 2009-11-06
is thunar causing X to freeze or is it just thunar  crashing?
If its crashing do you get any output in the terminal?

---

### Post by badgethefarmer on 2009-11-06
it is not thunar causing the crashes because gnome-commander and pcmanfm crashes too. 

when i type thunar on the terminal and crashes, there is no output or error message.

---

### Post by P4man on 2009-11-06
ok wild guess.. can you post the output of

```
df -h
``` ?

---

### Post by Bunnybugs on 2009-11-06
What did I miss?

Xubuntu, with Gnome-desktop files?

And if you try to add the menu-buttons to another bar?

I've got a third bar at the right of the screen, this bar contains easy use buttons... but you can add the menu to that one as well

---

### Post by badgethefarmer on 2009-11-06
> **P4man said:**
> ok wild guess.. can you post the output of

```
df -h
``` ?

i have tried it. it showed me my available and used spaces.

sorry, i couldnt post the result. diff machine i am using right now.

---

### Post by P4man on 2009-11-06
> **badgethefarmer said:**
> i have tried it. it showed me my available and used spaces.

sorry, i couldnt post the result. diff machine i am using right now.

well thats exactly what I wanted to see, because im wondering if you are not suffering from a full root partition. None of the %s were close to 100%?

---

### Post by badgethefarmer on 2009-11-06
> **P4man said:**
> well thats exactly what I wanted to see, because im wondering if you are not suffering from a full root partition. None of the %s were close to 100%?

None. The closest was at 61%. i am assuming that was the total of what i have used up my HD so far.

i fired up thunar and it was not [yet] crashing so i am hanging on it as of now. 

i cannot say this is resolved yet but once i get to back up all my files, ill be reformatting that machine w/ a karmic [ubuntu this time]. 

ill bump this thread or make a new one if i need more help.

thanks to P4man for the help and for the other guy who suggested something. [forgot your name]

---

