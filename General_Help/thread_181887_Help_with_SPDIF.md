---
title: "Help with SPDIF"
date: 2006-05-24
forum: General Help
---

### Post by jay_cee on 2006-05-24
Hi - I'm going nuts here trying to understand how SPDIF audio output works. I'm using SPDIF output from a Shuttle SK43g system. SPDIF audio works perfectly when playing DVDs through Totem. However I can't get _any_ sound out of any other applications (Kaffeine, xmms, KDE) and I can't get any sound when I'm playing other audio files (mp3, etc) through Totem. If someone could give me a few basic debugging pointers, I'd be very appreciative! It obviously works (DVDs via Totem), but I must have some other audio device settings not quite right. Thanks - J

---

### Post by warp99 on 2006-05-26
Very easy to change. Go to your System Settings > Sound & Multimedia > Sound System Configuration > then click the "Hardware" tab and do the following:

Uncheck "Full Duplex"
Check "Use Custom Sampling Rate" and choose 48000 Hz from the drop down box.
Under "Quality" choose "16 bits"
Check "Overide Device Location" and in the dialog box type "spdif", no quotes.

Click back to the "General" tab
Check "Auto-Suspend if idle after" and put 1 second in the dialog box. Reason you ask?  We need KDE to release the spdif port to allow Totem and Kaffeine direct access to the port. Now you know why Totem works. :D 

Click test sound, the sound server will reload and you should have some sound. You may have to go into alsamixer and play with the IEC958 settings in order to produce some sound. 

WARNING: With spdif you will have no software sound level controls since the port is treated as a AC-3 Pass Through. You will have to control the sound with the volume controls on the speakers or use some other type of hardware for volume control.

Hint: You can also set Kaffeine to access the spdif if you use the xine engine. Go into setup and under speaker arrangement choose AC-3 Pass Through. :cool:

---

