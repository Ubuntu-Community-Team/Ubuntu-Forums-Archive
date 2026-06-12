---
title: "Internal mic not working with any software: Ubuntu 10.10 Acer Aspire D250 Netbook"
date: 2011-02-13
forum: General Help
---

### Post by doktabl4ck on 2011-02-13
Hello,

I have been having this issue for months now and I cannot seem to find a remedy for it. On my D250 my internal mic does not work at all. I mainly use Skype and I have been trying to find an answer to my problem for months. I've seen different posts as how to try and fix the issue but I cannot seem to get it to work. Is there anybody that has any ideas? Much help would be greatly appreciated! :)

---

### Post by ajgreeny on 2011-02-13
Check in ```
alsamixer
``` in terminal that the mic is not muted, and also check in pulseaudio volume control the same thing.
ALSAMIXER
Run alsamixer in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "Playback" to "Capture" to "All".
Esc will save and exit.

---

### Post by doktabl4ck on 2011-02-13
So I tried what you said with different variations on the mixer and the mic still doesn't work. A friend of mine said that on his windows version, in the options it has an audio setting you can change. Well when I looked into the options menu for Ubuntu Skype, there's no such option. If the mic is not turned on in Skype then it won't work. Is there a way to get out of the beta version of Linux Skype or possibly get an update for the beta to get that option to check if the mic is even on?

---

### Post by ajgreeny on 2011-02-14
Click on your volume control icon and open Sound Preferences > Applications tab.  Now open skype and use **Skype Call Test**.  Whilst this is happening have a look at the sound preferences window to check that the application volume level is set high enough, (see screenshot) and that the input tab level is high and you can see the level indicator flashing with sound activity while you speak into the mic.

---

### Post by wrknight on 2011-07-01
If a solution hasn't been reported already, here's one that has worked on multiple Acer netbooks.  

From the applications menu, select Sound and Video > PulseAudio Device Chooser.  It will not appear to open, so look for the applet up on the task bar.  Pull down the menu from the applet and select Volume Control.  Then select the Input Devices Tab.  You will see the Internal Audio Analog Stereo icon and two channel controls.  Unlock the channel controls so they can be controlled separately.  Slide one control to the "off" position and leave the other channel at 100%.  It doesn't matter which channel you turn off, but definitely leave one off and the other on. You will now notice the volume meter responds to sounds.  Close the applet and now you can test with Skype or any other application that requires input from the internal microphone.

For some bizarre reason, the Pulse Audio software for the stereo input in Ubuntu 10.10 (and some other versions) processes inputs from the single source internal microphone in both channels and then adds them negatively so they cancel each other out.  Turning off one of the channels eliminates the the problem.

---

