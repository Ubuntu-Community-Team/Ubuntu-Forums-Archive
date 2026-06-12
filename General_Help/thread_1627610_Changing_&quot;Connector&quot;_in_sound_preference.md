---
title: "Changing &quot;Connector&quot; in sound preferences drops volume in ALSA"
date: 2010-11-21
forum: General Help
---

### Post by Exp HP on 2010-11-21
I got a new sound card for my laptop since my sound is broken.  This "new sound card" is actually just a cheapo USB dongle that you can stick a pair of headphones into.

After booting into Linux, I opened **Sound Preferences**, went to the **Output** tab, and selected **C-Media USB Audio Device**.

[IMG]http://imgur.com/so3Hm.png[/IMG]

*Yay, sound!  Hooray!  Ooooh, I wonder what this thing does?*

[IMG]http://imgur.com/BATDC.png[/IMG]

(loses sound)  *Oops, guess Analog Output's no good.*
(changes it back to Analog Speakers)  *Huh.  Still no sound.*
(kills and restarts Pulseaudio)
(takes the USB sound card out and puts it back in)
(restarts the computer)

Nothing was working. Changing this one little option made me irreversibly lose sound.

Then, right before I was about to post here asking you guys about it, I decided on a whim to check alsamixer.  I opened alsamixer, hit F6, and selected the new device.

[IMG]http://imgur.com/JP8L6.png[/IMG]

Ohhhhhhhhhh.

Okay, I get it now.  Changing the Connector in Sound Preferences to "Analog Output" sets the speaker volume in ALSA to 0, and the only way to resolve this is to open ALSAMixer and bring the volume back up yourself.

...wait, what?  Why?

Can I prevent this?

---

### Post by dcstar on 2010-11-21
> **Exp HP said:**
> I got a new sound card for my laptop since my sound is broken.  This "new sound card" is actually just a cheapo USB dongle that you can stick a pair of headphones into.
.......
Okay, I get it now.  Changing the Connector in Sound Preferences to "Analog Output" sets the speaker volume in ALSA to 0, and the only way to resolve this is to open ALSAMixer and bring the volume back up yourself.

...wait, what?  Why?

Can I prevent this?

Probably not, report it as a bug using the appropriate methods.

---

### Post by Exp HP on 2010-11-22
Well, what is this a bug with?  ALSA?
If this is a bug, I probably should report it, but I've never used the bug databases before, and I would need more information about it before I post it. For instance, *is anybody else affected by this?*
But I'm not sure if this is actually a bug.

It's worth noting that I found another way to trigger this volume-dropping behavior. I wish I noticed this before posting the topic, frankly:

*Sound is also lost if I close my laptop (i.e. enter sleep mode).*
When my laptop wakes, ALSAMixer changes to say the message "**The sound device was unplugged. Press F6 to select another sound card**".  Once I do select my sound card, I see that the volume is at 0.

---

