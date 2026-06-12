---
title: "Audio stopped working"
date: 2009-08-18
forum: General Help
---

### Post by dabansal on 2009-08-18
Hi Folks,

I have ubuntu installed on my machine and one fine day all of a sudden, my laptop stopped producing sound. It was kept on bed, so by any means, is overheating could be a possible cause or any other reason for such a behaviour. Although it is working fine with headphones, but not with in-built speakers. Please help. Any help will be highly appreciated.

Thanks and Regards,
Dheeraj Bansal

---

### Post by Dakiraun on 2009-08-18
My laptop occasionally seems to forget how to do sound as well (albiet it's a cursed Compaq R3000 with a troubled nForce3 chipset).  There is no exact way to fix it that I have found - sometimes a couple reboots works, sometimes I need to do it 20 times while trying to reinstall the PulseAudio drivers and systems.  It's very odd.  

What you might try is booting up the system on a couple LiveCDs - Ubuntu and maybe Puppy Linux and see if the sound is present on the LiveCD.  If so, then at least you know your sound is fine, and it's a matter of getting the sub-system working again in the main install.

---

### Post by dabansal on 2009-08-18
Hi,

As I had mentioned earlier that I had used headphones with it and it is working fine, problem lies with in-built speakers only. 

Thanks and Regards,
Dheeraj Bansal

---

### Post by Dakiraun on 2009-08-18
Ah - that might be easier then.  Ubuntu uses separate volume controllers on many systems for the speakers and headphones.  It may be possible that your speaker volume has been lowered or muted, while the headphones are not.  Click on the volume control icon in the system tray, then on preferences.  Check to see there's no mute symbol on the master output, or that master output isn't turned down too low.  Depending on if it was configured or not, you may also see a separate slider for the headphones.  If you don't, clicking preferences here should let you add it if the driver for your card supports it.

---

### Post by birdy on 2009-09-01
I have the same problem as the OP. A week ago, or so, speaker sound output stopped working - I can only get sound out through the headphone jack now. I have both "speakers" and "headphones" checked in the Volume Control.

---

### Post by Eder Santos on 2009-09-01
In your gnome-terminal type alsamixer and check.

---

### Post by birdy on 2009-09-01
Check what?

Please be more specific.

As I said, "speaker" is checked in volume control. alsamixer also indicates that "speaker" is enabled. On the side, how do you toggle headphone and speaker on/off in alsamixer?

Thanks,

Andreas

---

### Post by birdy on 2009-09-17
My problem disappeared when I started to jiggle around with pavucontrol (Applications / Sound & Video / PulseAudio Volume Control) . Not sure what I did, but after having played with it at one point, while on headphones, I noticed later that the speakers where also working.

---

