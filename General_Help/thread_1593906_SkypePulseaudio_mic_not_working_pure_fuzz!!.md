---
title: "Skype/Pulseaudio mic not working: pure fuzz!!"
date: 2010-10-11
forum: General Help
---

### Post by Bucky Ball on 2010-10-11
Hi all,

I had a rather long conversation with myself on another thread trying to fix my problem and now it has transformed into another problem which probably warrants a new thread.

I am using 8.04, Pulseaudio, Microsoft Lifechat USB headset and Skype on a Compaq 210. Pulse works fine for everything else. One day, it just stopped working for no apparent reason (only on the Skype mic) so I uninstalled and went back to ALSA (for a few reasons) but couldn't get that working either so now back to square one.

When I boot Skype, all goes well, can place a test call, no errors. But on playback of the message it's pure fuzz, basically white noise, no sign of my voice. I've twiddled with just about every volume control and toggle I can find and then some, but nothing. Another interesting thing; Pulse is now NOT working unless I input 'pulseaudio -D' in a terminal after boot. Then it seems to be okay, 'cept the mic. 

Strange as the mic works perfectly and crystal clear in Sound Recorder. No probs.

So:
1/ How do I replace the recorded white noise in a Skype test call with my own mellifluous tones and;
2/ Where do I put 'pulseaudio -D' (what file) so it will be read and turn pulse on at boot?

ALL ideas welcome. I'm getting kinda lonely out here. ;(

Using Skype 2.1.0.47 (I know there is a newer version, .87 I think, but that was even more problematic). Another strange thing; the newer version (.87?) worked flawlessly for months before the mic just one day died (ONLY in Skype). As explained on my last thread; wife's uni/entertainment machine and me being the house computer dude, one of the reasons we use Linux is so I am not fixing Windows problems constantly. I only go near this machine when something goes pear-shaped so that is rarely. My wife doesn't tweak with her computer AT ALL.

HELP! Sound issues on this machine have been pretty much constant and I am really sick of it. I have two desktops running ALSA and Skype flawlessly with any USB headset AND they can ring incoming calls through the external speakers and you can take the call through the headset, something that is seemingly impossible for some reason in Pulse. Despite its bells and whistles, this is a serious oversight by Pulse developers in my opinion. (Unless I'm missing something and I've have searched for hours trying to fix THAT little mystery).

*** Just as an added bonus, now when I try to open Pulseaudio Volume Control, the GUI flashes on then disappears. Damn, why is it this hard??? I have literally spent probably a fortnight full-time over the last six months just on the sound. Sheesh.

---

### Post by Bucky Ball on 2010-10-12
Well, step closer than I was three weeks ago. Got it all working with regular line in/out plug headphones. Now my problem is getting the ring through the speakers and only the call through the headphones. I have found no solution for this, either.

Time for another thread.

---

