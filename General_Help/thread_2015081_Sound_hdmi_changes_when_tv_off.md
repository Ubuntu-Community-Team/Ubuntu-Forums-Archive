---
title: "Sound hdmi changes when tv off"
date: 2012-07-02
forum: General Help
---

### Post by CrusaderAD on 2012-07-02
Ive got a strange problem here. I have a video card running with hdmi and it's plugged into my tv. The sound works fine when I first boot up. But when I turn the tv off and back on, the hdmi sound no longer works and is not an option in the sound menu. It won't work unless I reboot. Any ideas on keeping it on regardless of whether or not the tv gets turned off?

---

### Post by papibe on 2012-07-02
Hi CerealCypher.

This is not a perfect solution to your problem, but try restarting pulseaudio to see if either the sounds come up again, or at least it appears again on the sound menu:
```
pulseaudio --kill
```
Give it a few seconds and check.
Regards.

---

### Post by CrusaderAD on 2012-07-03
> **papibe said:**
> Hi CerealCypher.

This is not a perfect solution to your problem, but try restarting pulseaudio to see if either the sounds come up again, or at least it appears again on the sound menu:
```
pulseaudio --kill
```
Give it a few seconds and check.
Regards.

Tried your code in terminal, no effect :(

---

### Post by CrusaderAD on 2012-07-10
Got an update. The sound will come back if I log out and back in again. Better than rebooting completely I suppose.

---

### Post by staffann on 2012-07-20
I have exactly the same problem. Doesn't anyone know what causes this or how it can be fixed/worked around?
I use my Asus E45M1 Deluxe as a media player. I have XBMC installed on it and ideally don't have to have any keyboard or mouse connected, just my Android phone as a remote. Considering that, having to log out and in every time I turn on the TV isn't an option!

---

### Post by CrusaderAD on 2012-07-20
I haven't seen or come up with a fix. You could leave your TV on and activate the screensaver instead of shutting it down. I just keep logging out and back in. I noticed when you log out and turn off the TV, then turn it back on... you need to log in, log out, log back in for it to work again. Frustrating.

---

### Post by pqwoerituytrueiwoq on 2012-07-20
i have a similar issues when i turn my screen off my theme manager crashes
you could try using analog audio
[http://ubuntuforums.org/showpost.php?p=11712722&postcount=12](http://ubuntuforums.org/showpost.php?p=11712722&postcount=12)
the tv will think you are using dvi and use the pc audio input for audio
on my system my kernel does not support hdmi audio on my gpu, but i am not ready to leave my 10.04 install

---

