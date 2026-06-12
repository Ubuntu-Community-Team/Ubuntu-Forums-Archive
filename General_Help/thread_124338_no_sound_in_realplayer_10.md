---
title: "no sound in realplayer 10"
date: 2006-02-01
forum: General Help
---

### Post by leveliv on 2006-02-01
hello I have Realplayer 10 GOLD ...that I installed from an RPM using alien...playback with streaming video is awesome quality and seamless but ..there is no sound :'( can I fix this some how or is there another player that will play my saved realplayer streams?

---

### Post by ubuntuross on 2006-02-06
I have this same exact problem with the only exception being that I didn't use the RPM.

---

### Post by dcstar on 2006-02-06
[QUOTE=ubuntuross]I have this same exact problem with the only exception being that I didn't use the RPM.[/QUOTE]
See my post here:

[http://ubuntuforums.org/showthread.php?t=123370](http://ubuntuforums.org/showthread.php?t=123370)

---

### Post by ubuntuross on 2006-02-06
dcstar,

I've already installed exactly how your post described; however, your post doesn't address of the issue of video but no sound.

I think perhaps RealPlayer is trying to use my onboard sound, but it needs to be using my Sound Blaster Live card.  I can't find anywhere in my BIOS or a jumper on the board to disable the onboard sound.  Does anyone know if I can somehow "disable" the onboard sound device similar to how you can disable a device in Windows?

Thanks.

---

### Post by dcstar on 2006-02-06
[QUOTE=ubuntuross]dcstar,

I've already installed exactly how your post described; however, your post doesn't address of the issue of video but no sound.

I think perhaps RealPlayer is trying to use my onboard sound, but it needs to be using my Sound Blaster Live card.  I can't find anywhere in my BIOS or a jumper on the board to disable the onboard sound.  Does anyone know if I can somehow "disable" the onboard sound device similar to how you can disable a device in Windows?

Thanks.[/QUOTE]
Does sound work with other things?

---

### Post by ubuntuross on 2006-02-06
My system sounds work after I changed it to use the SB Live card instead of the onboard sound.  Same thing for XMMS.  I assume I need to do the same thing with RealPlayer, but I see no option to such a thing.

Thanks.

---

### Post by dcstar on 2006-02-07
[QUOTE=ubuntuross]My system sounds work after I changed it to use the SB Live card instead of the onboard sound.  Same thing for XMMS.  I assume I need to do the same thing with RealPlayer, but I see no option to such a thing.

Thanks.[/QUOTE]
Possibly these could be of use:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)
[http://ubuntuforums.org/showthread.php?t=88203](http://ubuntuforums.org/showthread.php?t=88203)

---

### Post by Vanish00 on 2007-01-20
I tried looking into those links on getting sound in realplayer, but I'm still to new to figure out the problem myself.  Anybody figure out the source of the problem? and the fix?

---

### Post by david_2001 on 2007-01-20
Did everybody with no sound in RealPlayer make sure that they installed alsa-oss first?  I know that I'm asking a silly question but I don't see it mentioned except in one of the cross-referenced threads.

---

### Post by Vanish00 on 2007-01-20
I did verify that alsa-oss is installed and I restarted my computer.  Now 1 good thing is that I got sound now but its distorted like it's being streamed with static in the background.

---

### Post by drjzzz on 2007-01-26
Sound worked fine overall but I had no sound from the newly-installed Realplayer.  I went to the "System/Preferences/Sound", changed from "autodetect" (the test sound worked) to "OSS" (the test sound still worked).  Upon restarting, Realplayer sound now works, sounds fine.  Simple, and I hope it works for you.

---

