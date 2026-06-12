---
title: "No sound in skype!!"
date: 2010-11-27
forum: General Help
---

### Post by Lisimelis on 2010-11-27
Well my problem is this. I am trying to use Skype beta on my acer aspire one with ubuntu 10.10. The video runs brilliantly and i can also here my wife from the other end but she cannot hear me!! Apparently something is fishy with my mic input. I tried alsamixer and everything is in unmute. My alsa version is 1.0.23. The only think she hears is a loud hissing noise which is normally my bat voice but she doesnt need to know that. Any help please???? I can record my voice in the sound recorder but nothing comes out in Skype!

---

### Post by Tobeus on 2010-11-27
If I remember correctly, there is a test call you can do in Skype to see if it is your mic.  Run the test call, and speak when she tells you to speak.  Then see if you can hear yourself when she plays back your audio.  If you can hear yourself on the test call, then the problem is likely on your wife's end, not yours.  This will at least make sure you know where the problem is.

If all she is hearing is static, then it is possible that her sound playback is choosing the digital out rather than the regular sound system for playback.  I would have her do the skype test call as well and see if she can hear the test voice, or if it is static as well.

Good luck!

---

### Post by Lisimelis on 2010-11-27
No when i ran the test call i cannot hear my self speak so it must be own problem!!! Any suggestions?

---

### Post by Tobeus on 2010-11-27
Okay, do you see your sound speaker icon in the notifier area on your upper bar?  Left click on it and go to Sound Preferences...

Then click on the Input tab, and you should see a pulldown menu for Connector:

This is where you can choose different mic input plugs to use and you can also adjust the input levels here.  For example, my Skype does not work on Microphone 1, but needs to be on Microphone 2 to receive any input.  Also, the input volume had to be turned up a bit in order for any volume to be recorded.

Play with these settings and use the test call and see if you can get anything to be recorded.

Hope this helps!

---

### Post by CoolJohnB on 2010-11-27
Also in Alsamixer press F4 for capture and make sure the volume levels are up on the mic's and also capture.

Sometimes it helps in Skype>Options>Sound devices to take the tick out of the box that says; "Let Skype automatically adjust sound levels"

Hope you get it sorted.

---

### Post by Lisimelis on 2010-11-27
SOLVED with external mic....thanks all!!!!

---

### Post by lemmy15 on 2010-11-27
> **Tobeus said:**
> Okay, do you see your sound speaker icon in the notifier area on your upper bar?  Left click on it and go to Sound Preferences...

Then click on the Input tab, and you should see a pulldown menu for Connector:

This is where you can choose different mic input plugs to use and you can also adjust the input levels here.  For example, my Skype does not work on Microphone 1, but needs to be on Microphone 2 to receive any input.  Also, the input volume had to be turned up a bit in order for any volume to be recorded.

Play with these settings and use the test call and see if you can get anything to be recorded.

Hope this helps!


Thanks from me, too!  Funny how in the end it had nothing to do with Skype per se.  The real proof in the pudding will come tomorrow when I try to call somebody (too late right now).

---

