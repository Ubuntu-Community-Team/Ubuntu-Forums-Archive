---
title: "No sound?"
date: 2009-08-10
forum: General Help
---

### Post by inaety on 2009-08-10
I updated my system to 9.04 without any problems and now my sound won't work...for the most part. Amarok2 plays my music and Dragon Player will play my videos without ANY problem.  Mplayer, firefox, etc nothing else will play.  I'd like to be able to watch flash videos and such, and, also, use mplayer in general.  I searched and found information about setting my settings to use PulseAudio and use their output manager, but that was to no avail.

Any help?

---

### Post by inaety on 2009-08-10
bump

---

### Post by starcraft.man on 2009-08-10
I'm gonna take a wild guess without explanation, I'm feeling lucky tonight.

Right click on the volume icon in the sys tray of panel and Show Kmixer Window. Then, set all the sliders there to maximum, including especially the PCM slider, ensure it's 100%. Close any open browser, then open it up again and play flash media to hearts content.

---

### Post by inaety on 2009-08-10
> **starcraft.man said:**
> I'm gonna take a wild guess without explanation, I'm feeling lucky tonight.

Right click on the volume icon in the sys tray of panel and Show Kmixer Window. Then, set all the sliders there to maximum, including especially the PCM slider, ensure it's 100%. Close any open browser, then open it up again and play flash media to hearts content.

Didn't work, thanks though

---

### Post by starcraft.man on 2009-08-10
> **inaety said:**
> Didn't work, thanks though

My next suspicion then would be some sort of undisclosed error during upgrade (they happen) or a conflict with something left over or unaccounted. To rule this out, insert the live disk and boot into Kubuntu live. Then, test all the things that usually don't work. If they work out of box, I'd assume some upgrade problem.

Additionally, while booted into live and to your local install after, go to the Multimedia menu KMenu > System Settings (favourites page) > Multimedia > Device Preferences (default tab). Then you'll see to the right, several different possible subsystems, like pulse audio or HDA. Each of these is a different system you can use to play, to the left you'll see different categories that can be set to different settings. Note the one at top of list and try and fiddle with settings globally. Bump the second one up to first spot (prefer or defer button at bottom right) and then at bottom left Apply Device List to... click it and apply to all sections. Then test problems again, repeat with trial and error until all problems fixed. If this doesn't resolve issue, it'll be necessary to take a close look at hardware, most motherboard's are supported well with audio because of the HDA specification on most modern ones.

---

### Post by inaety on 2009-08-10
> **starcraft.man said:**
> My next suspicion then would be some sort of undisclosed error during upgrade (they happen) or a conflict with something left over or unaccounted. To rule this out, insert the live disk and boot into Kubuntu live. Then, test all the things that usually don't work. If they work out of box, I'd assume some upgrade problem.

Additionally, while booted into live and to your local install after, go to the Multimedia menu KMenu > System Settings (favourites page) > Multimedia > Device Preferences (default tab). Then you'll see to the right, several different possible subsystems, like pulse audio or HDA. Each of these is a different system you can use to play, to the left you'll see different categories that can be set to different settings. Note the one at top of list and try and fiddle with settings globally. Bump the second one up to first spot (prefer or defer button at bottom right) and then at bottom left Apply Device List to... click it and apply to all sections. Then test problems again, repeat with trial and error until all problems fixed. If this doesn't resolve issue, it'll be necessary to take a close look at hardware, most motherboard's are supported well with audio because of the HDA specification on most modern ones.

I'm having an issue seeing that its because of hardware since I can, and am at this moment, listening to Amarok play music.  Every past version of Ubuntu has had no problem in playing sound, and since I am not SoundBlaster equipped or anything I dont need any special extra work.  Its probably an upgrade issue like you said, since my system settings is all using my Intel chip which is what currently works

---

