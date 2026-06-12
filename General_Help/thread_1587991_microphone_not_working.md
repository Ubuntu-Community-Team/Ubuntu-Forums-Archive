---
title: "microphone not working"
date: 2010-10-04
forum: General Help
---

### Post by mather25 on 2010-10-04
just switched over to ubuntu.  wife tried to make a call back to the states over skype, and the microphone is not working.  please humor a noob...help?

---

### Post by MooPi on 2010-10-04
You'll need to open the Options menu on the lower left of the panel for Skype. Then move to the default device for the Microphone. Select the appropriate device and you should be able to record and use the mic.

---

### Post by stoobers on 2010-10-08
Ok.  I had a similar problem.  Here is how I eventually fixed it.

1. skype wants to use "pulseaudio".  This is GOOD, no matter what you read.  You can see this in the "options" section of skype.  I got there by launching skype, logging in, then opposite clicking the skype icon in the system tray at the bottom right and picking "options", then "sound devices".  Under microphone, it should say "pulseaudio server (local)".  The location of your skype icon in the system tray may vary. 

Second, you need to get your microphone working.  You have to "turn it on".  Sounds simple, but it isn't obvious.  First, you need to activate it at the ALSA level (???) then at the pulseaudio level.  You need to do both!  There seem to be TWO on switches.  I don't know why these aren't integrated, but they are not.

So you run: kmix.  If you don't have it installed, you can run: alsamixer, but I think kmix is easier.  In kmix, you pick "settings" then "configure channels".  Then drag "mic" and "mic boost" from the left to the right and click ok.  In kmix, make sure the "mic" is not muted, and turn it up all the way.  Then move the "mic boost" up a bit.  You should hear some feedback.  If you talk into the mic, you will hear yourself on the computer speakers.  That is GOOD.

Then, you need to run: pavucontrol  This will let you activate the mic in pulseaudio.  under "input devices" pick "microphone 1" and UNCLICK mute!!!!!  If you talk into the mic, you will see the little blue line start to move with your sound.  This is GOOD.

After that, I just started up skype.  By default, the mic is muted in TWO PLACES!!!!

Oh, Linux!  Fie, for shame!

But now it works.

SUCCESS!
:P

---

