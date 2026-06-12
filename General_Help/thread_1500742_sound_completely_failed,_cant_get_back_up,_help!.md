---
title: "sound completely failed, cant get back up, help!"
date: 2010-06-03
forum: General Help
---

### Post by xfearxnxloathing on 2010-06-03
i've had this 64bit installation up and running for a week then suddenly the sound went out on me while listening to a song via songbird.  i have not installed anything new or changed any configurations, haven't even messed with the volume period.  

i rebooted, no sound, not even on start up.

i typed in ALSA in the Ubuntu Software Center and installed it, rebooted again and still nothing.  what's going on here?   

i can provide additional information, just tell me what commands to type.

thnx

---

### Post by ThesaurusRex on 2010-06-03
Can you check the speakers on another computer? My speakers went out on me a few months ago, and the problem ended up being hardware.

---

### Post by xfearxnxloathing on 2010-06-03
> **ThesaurusRex said:**
> Can you check the speakers on another computer? My speakers went out on me a few months ago, and the problem ended up being hardware.

i can try this, hope it isnt tho..  i'll get back to you.

---

### Post by ajgreeny on 2010-06-03
Use ```
alsamixer
``` in terminal to check that sound levels are not muted or set too low; this seems to be the case quite often after updates.

---

### Post by xfearxnxloathing on 2010-06-03
> **ajgreeny said:**
> Use ```
alsamixer
``` in terminal to check that sound levels are not muted or set too low; this seems to be the case quite often after updates.

apparently everything was muted..  sry guys!

[IMG]http://i556.photobucket.com/albums/ss10/xfearxnxloathing/Screenshot-2.png[/IMG]

---

