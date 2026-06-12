---
title: "Noob Needs Help With sound problem please"
date: 2009-11-08
forum: General Help
---

### Post by Davidwclausen on 2009-11-08
Hello I am fairly new to the Ubuntu Community. I have just upgraded to Ubuntu.9.10 from whatever the previous version was. I am using a Toshiba Satellite A105-S4064 with the RealtekALC861 onboard Audio. My sound worked fine until I upgraded. I never Had any problems with my old version but I really would like to get my sound working again. If anyway could help me figure out my problem It would be Greatly Appreciated.

---

### Post by ajgreeny on 2009-11-08
It could be a bit dangerous to add your email and IM names etc to a forum post.  I would remove them if I were you, and wait for a response on the forum the way most people do things.

---

### Post by Davidwclausen on 2009-11-08
THanks for the Advice. I got my emails outta there but I still need helps getting the sound to work. So if anyone has any Ideas please let me know

---

### Post by sgtmcc on 2009-11-08
Does alasmixer or your gui volume mixer show your soundcard to be there?
What is the output of asoundconf list ? Do you have a usb headset also or just your speakers? Might want to make sure your card is not muted in alsamixer when you are in there

---

### Post by Davidwclausen on 2009-11-08
It does show my sound card in alas and it is not muted i am also using just the speakers on the laptop as well as a headset that has a 3.5mm jack also please remember I am really new to ubuntu and linux in general the sound was working before I upgraded but now it is not. I can also provide you with any information needed as long as you can help walk me through how to get it

---

### Post by Digital Magi on 2009-11-12
I have had this same problem, same model of laptop as you. Last time it happened was five minutes ago :(

After some experimentation it looks like there is something odd about the way the sound hardware is detected at boot as it seems to change.

I did a clean install after a fresh format, all hardware detected and installed correctly including sounds. Worked fine for a week or so, then the sound just stopped. A check of sound properties (right-clicking on the volume icon) showed my sound card no longer detected as a device. Sound output was listed as "dummy output" with full volume. The device showed up in hardinfo as "Intel HDA device" but in the audio preference just as "dummy output".

I had done some updates and software installs, figured I might have broken something. Since I use a separate /home partition, I just wiped the boot partition and reinstalled. Once again sound worked.

Tonight I booted up, once again no sound, again with "dummy output". No hardware detected in the listing in hardinfo.

On a whim, I rebooted and chose "failsafe Gnome". No sound hardware detected at all, no volume icon. After another reboot sound was returned, and the device now shows up as "Intel Corporation 82801G".

Is hardware re-detected on each boot? Any way to find the setup that works and lock that setup in so it won't be changed?

---

### Post by MichealH on 2009-11-12
You may want to try this:
[Audio Gotchas in 9.10 Tread]("http://ubuntuforums.org/showthread.php?t=1307019")

---

### Post by michaelzap on 2009-11-12
If you have a proprietary modem driver listed in System -> Hardware Drivers try removing it. That immediately made my sound card appear in the Sound panel. Before that all I saw was "Dummy Output".

There are some other good tips [here]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html").

---

### Post by Digital Magi on 2009-11-12
Thanks michaelzap! That was an instant fix. Some kind of conflict between the two devices I guess. No big loss about the modem, can't recall the last time I actually used dialup anyway.

---

### Post by michaelzap on 2009-11-12
> **Digital Magi said:**
> Thanks michaelzap! That was an instant fix. Some kind of conflict between the two devices I guess. No big loss about the modem, can't recall the last time I actually used dialup anyway.

Excellent! Please mark the thread as solved (oh - I see now that you didn't start the thread...).

---

### Post by Digital Magi on 2009-11-12
I'm not the OP, just a piggy-back with the same issue :) He has to mark it solved, right?

---

### Post by Davidwclausen on 2009-11-12
I started it I am currently at work and will try all of your suggestions when I get home. Thank you all for the help and I will let you all know if it works

---

