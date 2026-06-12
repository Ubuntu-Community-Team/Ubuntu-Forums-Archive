---
title: "Sound lost"
date: 2012-04-18
forum: General Help
---

### Post by Parzi on 2012-04-18
Removed Windows 7 and installed Ubuntu 10.04 to my HP 635 laptop. Everything else seems to work okay but all sounds are lost. Any ideas how to fix this?

---

### Post by Tamlynmac on 2012-04-18
Have you looked at your "system/preferences/sound"? Initially, when opening the sound preferences window, on the top will be a slider for "output volume" If it's all the way to the left and/or if the "Mute" box is checked, you'll not hear any sound. Uncheck the mute box and/or move the slider to about "unamplified 100%". If your trying to hear sound effects, then on the sound effects tab, make sure the the alert volume is turned up & unmuted.

On the hardware tab, you should see your sound card listed.

If your still experiencing problems, you might also try checking your "system/administration/hardware drivers" for a audio driver and installed it.

Good Luck & hope this helps.

---

### Post by Parzi on 2012-04-19
Nothing is muted. Output volume is 100%. Nothing works.

From hardware drivers I find only : "No proprietary drivers are in use on this system".

Might his be the problem?

---

### Post by Tamlynmac on 2012-04-19
I had this happen on a couple of HP laptops when installing 10.04. I went  into Synaptic Package Manager and installed the "alsamixergui" and  rebooted. After which it worked fine.

One other quick question, what is listed as the device or devices in the "Sound Preferences" output tab? One other thing you can check while in Sound Preferences output tab, is the connector - try changing it from analog speakers to head phone and back again - then reboot - assuming something is listed there.

---

### Post by Parzi on 2012-04-21
Installing alsamixergui didnt help.

from sound preferences i can find:

Hardware

internal Audio
1 input 
Analog stereo input

internal audio
1 output
digital stereo (hdmi) output


Output

Internal audio digital stereo(hdmi)
stereo

---

### Post by mörgæs on 2012-04-21
Why did you choose 10.04 and not one of the 11.10's?

---

### Post by Parzi on 2012-04-21
11.10 had some problems with graphics.  Moving windows e.g caused window to multiply itself and things got stucked for a period of time etc.

---

### Post by mörgæs on 2012-04-22
But how did the sound work in 11.10?

---

### Post by Parzi on 2012-04-22
Sound worked if I rember correctly.

---

### Post by cyncicle on 2012-04-22
I had a sound problem with a Dell laptop a year or so ago, and it ended up being an issue with ALSA and Intel HDA not playing well.

Might find your answer here: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by mörgæs on 2012-04-23
I would go for 11.10 (or 12.04) and try to fix the graphics problems here rather than struggling with 10.04. Have you tried X/Lubuntu?

---

