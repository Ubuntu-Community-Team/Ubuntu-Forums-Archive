---
title: "Sound problems."
date: 2010-05-08
forum: General Help
---

### Post by SirRedTooth on 2010-05-08
In Karmiac I used to have problems with my sound where only one application could play sound at once.

Then when I upgraded to lucid lynx sound always worked perfectly on Songbird but didn't work at all on firefox (flash and .mov format).
Firefox just wouldn't appear on the Applications tab on the sound prefrences

So then I decided to install this plugin:
[http://www.thelinuxdaily.com/2007/10/how-to-fix-the-no-sound-issue-in-firefox-flash/](http://www.thelinuxdaily.com/2007/10/how-to-fix-the-no-sound-issue-in-firefox-flash/)

Now sound does work on firefox, but only if I close songbird.
And when it does work there is like a 3 second lag time between the video and the sound.

---

### Post by P4man on 2010-05-08
Sounds like you uninstalled pulseaudio on karmic, and maybe the upgrade to lucid didnt install it or not properly. then you installled a .deb that does I dont know what, but which was made for ubuntu 7.04 and may even predate pulseaudio. IOW, Im not shocked you have problems.

Try running computer janitor to get rid of that last deb you installed. Then reinstall pulseaudio from synaptic and if you still have problems in flash then, maybe reinstall flash from adobe's website as Im guessing you also "messed" with flash on karmic, probably trying to solve whatever audio problem you had then.

---

### Post by SirRedTooth on 2010-05-08
I never remember uninstaling pulseaudio.
I downloaded firefox using PlayOnLinux and everything works fine, it can even play audio at the same time as Songbird.
But its very very laggy and the reason I moved to ubuntu in the first place is because it runs faster.

---

### Post by worldofsimulacra on 2010-05-08
Similar issue here, except that I had sound all around when I first installed Lucid, then all browser sound went out after I installed the first pack of updates. Finally got around to working on it last night - I wish I would've found this patch! but I found this workaround on one of the development forums

> that does nothing, still had to change pin 19 amplifier setting to grd / hiz from numerical value for any sound.

with that done, am getting consistent sound and jack sense

which also worked, and it still works on reboot (fingers crossed).

---

