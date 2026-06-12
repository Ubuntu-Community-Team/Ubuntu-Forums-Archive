---
title: "Front Mic does not work!"
date: 2011-05-04
forum: General Help
---

### Post by Churk on 2011-05-04
Good afternoon everyone, first I'm from Brazil and I'm not very good in English, and this is the only forum I found Ubuntu, my problem is this: my front mic not working, only the the back entrance, which is more difficult to connect tras la Someone can tell me how I can work my microphone to faser near the front? my ubuntu is 4.11, and had tested all the devices and nothing but the same rear entrance ... thanks !

---

### Post by ajgreeny on 2011-05-04
"My ubuntu is 4.11"?

What does this mean please?  There is no Ubuntu 4.11, though there was a 4.10 way back in the misty days of October 2004, but this has not been active for about 6 years.

I suggest you update to a newer version, 10.04 (or 11.04 if you can manage the new desktop, Unity), and then follow the info below about alsamixer, which may allow you to unmute or raise the levels needed to get the microphone working.  You will probably find you have two mics showing and a "choose mic" from where you can set mic 1 or mic 2.

ALSAMIXER
Run alsamixer in terminal and check that the levels of outputs are not set too low.

Use the cursor keys to move from slider to slider, and raise and lower levels;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture" to "all".
Esc will save and exit.

---

