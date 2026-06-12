---
title: "Mic Not working"
date: 2012-04-12
forum: General Help
---

### Post by bennettg on 2012-04-12
Hello.  I've just completed a fresh install of lubuntu 11.10 on a hp mini 1116NR.  Everything works fine except the mic. no matter what program i test with, the mic is not working, even in skype....the speakers/sound work just fine.

i tried pavu control without success.  when i installed pulse audio and played with the inputs, it killed my speakers and didnt help the mic.  i had to uninstall pulse audio to get sound working again.  

i tried alsa mixer and it showed doc mic and rear mic as mic in, but i'm not sure what is happening.  i was able to take a screen shot.



can someone help this noob?

thanks in advance

---

### Post by Dude-PWB- on 2012-04-12
On my eeepc I had to install pavucontrol and then in the mic settings it showed 2 channels for the mic. I had to unlock the channels, and then turn one of the channels down to zero, keeping the other channel at full. It was like one channel was canceling out the other channel.

---

### Post by bennettg on 2012-04-13
> **Dude-PWB- said:**
> On my eeepc I had to install pavucontrol and then in the mic settings it showed 2 channels for the mic. I had to unlock the channels, and then turn one of the channels down to zero, keeping the other channel at full. It was like one channel was canceling out the other channel.

response appreciated, but it didnt work.

does anyone else have a suggestion?

---

### Post by bennettg on 2012-04-13
i got it to work.  hopefully this will help someone.

i uninstalled anything that had pulseaudio.

then opened a terminal and did sudo alsamixer

i played around the settings with the mic changing to line in and then went into the 2nd page by hitting tab or enter to change the line in mic settings so that they were not balanced  left at almost zero and right at alomst 90.  i had to use f1 to get help to determine which letter keys increased the left and decreased the right.  i did this for a few different bars.   i'd open alsa mixer again and take a screenshot, but i am afraid of losing my settings.

---

