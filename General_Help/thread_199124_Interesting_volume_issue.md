---
title: "Interesting volume issue"
date: 2006-06-18
forum: General Help
---

### Post by steveyeager on 2006-06-18
Dapper is great.  Almost everything works well.

I have a couple of minor issues.

First of all, the driver ubuntu uses for my onboard cmedia sound for my esc motherboard works well.  I have the volume at about 40% using the main volume control on the volume icon in the toolbar.  All is good.

However, I have a logitech multimedia keyboard.  When I press the multimedia keys, almost all work without modification.  Wow.  However, the volume buttons do something curious.  Using either increase or decrease volume invoke the graphical volume control and appear to work, but actually do not affect the volume of sound.  The percentage displayed on the volume icon in the task bar reads the same and any cd or sound played is not affected by the keyboard volume control.  So, what setting can I modify to correct this?

More importantly, some applications I have: Avidemux and Cinelerra both play  an mpeg file I have but very load.  It seems they play with no regard to the volume control whatsoever.  Please help me correct this.

Finally, strangely enough, totem plays the same mpeg file without any sound.  I am not certain what to address here, so please give me some suggestions.

This forum is fantastic.  I am anxious to correct these issues and continue to recommend Ubuntu to everyone (especially those who are hooked on windows!!).

---

### Post by steveyeager on 2006-06-18
OK, I found that the toolbar icon modifies the PCM audio volume and the keyboard modifies the Master Mono volume.  But, Totem still plays no audio at all.  And the same clip played in AviDemux, Audacity and Cinelerra have extremely loud volume - even though I have gone through every volume level in the Gnome Volume Control app is set to 33% or below.

So, what is Master Mono used for?

Why is Totem not playing audio?

And why are other apps playing so loud?

---

### Post by Riddian on 2006-06-20
I have exactly the same problem, different keyboard and different sound card however. In my case the volume keys used to work fine. My entire sound stopped worked before and I had to tell ALSA which device to use which bought back sound, then I had to set the volume control applet to control the right device and volume slider too. However there seems to be no way of setting up what volume is controlled by the volume keys as it's controlling exactly the same wrong device/slider that the volume control applet used to.

As for your other problems, Master mono probably isn't used for anything, I have a ton of volume sliders which have no function with my card. Totem might not be playing audio for codec reasons or perhaps the sound system totem is using isn't working? try the command "gstreamer-properties" and pick one that works. No idea about the loudness however, couldn't even hazard a guess sorry·

---

### Post by Riddian on 2006-06-20
Still no joy, been scouring the forums and have found several posts that describe exactly the same problem with no resolution whatsoever. Infact someone suggested that the volume controlled by the hot keys is hardcoded so there would be no chance of fixing it save editing the code and recompiling it.

[http://ubuntuforums.org/showthread.php?t=199579&highlight=volume+control]("http://ubuntuforums.org/showthread.php?t=199579&highlight=volume+control")
[http://ubuntuforums.org/showthread.php?p=1155376#post1155376]("http://ubuntuforums.org/showthread.php?p=1155376#post1155376")
[http://ubuntuforums.org/showthread.php?t=193936&highlight=volume+control]("http://ubuntuforums.org/showthread.php?t=193936&highlight=volume+control")
[http://ubuntuforums.org/showthread.php?t=198183&highlight=volume+control]("http://ubuntuforums.org/showthread.php?t=198183&highlight=volume+control")
[http://ubuntuforums.org/showthread.php?t=196197&highlight=volume+control]("http://ubuntuforums.org/showthread.php?t=196197&highlight=volume+control")
[http://ubuntuforums.org/showthread.php?t=196981&highlight=volume+control]("http://ubuntuforums.org/showthread.php?t=196981&highlight=volume+control")
[http://ubuntuforums.org/showthread.php?t=186712&highlight=hot+key+volume+control]("http://ubuntuforums.org/showthread.php?t=186712&highlight=hot+key+volume+control")
[http://ubuntuforums.org/showthread.php?t=84759&highlight=hot+key+volume+control]("http://ubuntuforums.org/showthread.php?t=84759&highlight=hot+key+volume+control")
[http://ubuntuforums.org/showthread.php?t=118077&highlight=hotkey+volume+control]("http://ubuntuforums.org/showthread.php?t=118077&highlight=hotkey+volume+control")

---

### Post by steveyeager on 2006-06-21
Very interesting.  

I ran 'gstreamer-properties'.  It showed me 3 output plugins: ALSA - Advanced Linux Sound Architecture, ESD - Enlightenment Sound Daemon, and OSS - Open Sound System.  When I tested each, ALSA and ESD played the test at a modest level - apparently it used the 33% volume set by one of the volume levels I set.  However, testing the OSS was played very loud!  Exactly the same as ALSA played the test when I turned the volume of PCM to 100%.  So, how can I control the volume of OSS?  It is possible that my applications use that volume.  So if I can set the OSS volume, I might just get this to work!!?!

Please help.

---

### Post by inigmatus on 2006-06-21
I'm adding my name to the list of those who have a keyboard that adjusts the Master Volume control, but since Master Volume does absolutely nothing, I have to go the alsamixer to adjust headphone or PCM volume to make any difference in volume level on my computer.

Can someone fix this? There's got to be a way to change the default sound control away from Master, but logically Master should be controlling all sound anyways, and yet it's not.

---

### Post by steveyeager on 2006-06-25
OK, I have gotten further.

OSS volume can only adjust either 100% or 0% and nothing in between.  And since AviDemux and Cinelerra both use OSS by default, it only plays at full volume.

However, I was able to alter AviDemux to use ESD, and that works great.  My toolbar volume control for PCM adjusts this volume correctly.  Cinelerra requires using the ALSA driver and can adjust the volume within the app, but the toolbar does not vary the volume at all.

So, 
1) why does OSS only have full volume or no volume?
2) why does my keyboard adjust ALSA master mono?
3) why does ALSA master mono not control any applicable volume?

Please help.

---

### Post by H.E. Pennypacker on 2006-07-06
[QUOTE=inigmatus]I'm adding my name to the list of those who have a keyboard that adjusts the Master Volume control, but since Master Volume does absolutely nothing, I have to go the alsamixer to adjust headphone or PCM volume to make any difference in volume level on my computer.

Can someone fix this? There's got to be a way to change the default sound control away from Master, but logically Master should be controlling all sound anyways, and yet it's not.[/QUOTE]

I am having the exact same problem, and when I right-click the volume icon, go to Properties, and select another device and track, it's still the same.  My FN on the keyboard will only work when I have no headphones on.  In other words, the FN keys only work on the laptop's speakers, and not "Master."

> 
2) why does my keyboard adjust ALSA master mono?

Change which track/device you want used by following the instructions I gave above.

---

