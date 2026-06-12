---
title: "A serious problem with skype on Ubuntu"
date: 2010-08-23
forum: General Help
---

### Post by vladcambridge on 2010-08-23
Hi, I am having the following problem - whenever I try to call anyone, after 10 seconds of conversation the sound output stops and I do not hear a thing. From this point onward I am unable to call anyone, the call simply does not start. Skype becomes a lot slower. My sound card magically disappears from System>Preferences>Sound>Hardware. When I close the app (skype) and then try to shut down the PC it tells me that skype isn't responding. If the PC is restarted however, everything goes back to normal.

The version of skype is 2.1.0.81
OS: Ubuntu 10.04
Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

I appreciate any help! Thanks!

---

### Post by vladcambridge on 2010-08-24
Please help guys, I am really desperate to solve this problem.

---

### Post by vladcambridge on 2010-08-24
The version of skype is 2.1.0.81

---

### Post by techunit on 2010-08-24
Well what sound card do you have... you aren't being very clear.

---

### Post by vladcambridge on 2010-08-24
Sorry about that, I thought the attached file would help.
Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

---

### Post by vladcambridge on 2010-08-24
Another thing, after a conversation lasts for ~10 sec and skype slows down, my chat messages do not reach the recipient. And, in fact, in most cases skype doesn't slow down, it simply freezes and I am forced to kill it.

---

### Post by vladcambridge on 2010-09-11
*bump*

---

### Post by vaccinus on 2010-09-15
Try first step from here (upgrading the ALSA sound system to the newest version):

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Cheers! :)

---

### Post by vladcambridge on 2010-09-24
> **vaccinus said:**
> Try first step from here (upgrading the ALSA sound system to the newest version):

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Cheers! :)

Thanks! It has in fact solved the problem!

---

