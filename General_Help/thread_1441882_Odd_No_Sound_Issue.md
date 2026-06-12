---
title: "Odd No Sound Issue"
date: 2010-03-29
forum: General Help
---

### Post by divinedark on 2010-03-29
Hello fellow linux brothers and sisters. I finally broke down and up graded from Hardy yesterday and I've been stumped ever since. My sound doesn't work at all. I can open up alsa mixer and see the sound is registering on the EQ. I can watch the levels change to the music, but nothing comes out of the speakers.

I've followed every script, reinstall, and patch I've found, but I;m not sure it has anything to do with the install. It sees the card and there is output. It's just not coming out of the proper channel.

I am a Ubuntu newb, so please be gentle. I love the system, but this is frustrating. Sound works in windows 7 perfectly. Just not here.

My chipset is 82804H and it's using the STAC92xx codec. The sound card is IDT 92HD71B8X. 

Thanks all in advance.

---

### Post by divinedark on 2010-03-29
Okay... I seem to inadvertently fixed the issue by switching over to Analog Audio Output. 

I guess these forums are magical. :D

---

### Post by tetsuo2010 on 2010-03-29
i am a newb as well, any ideas on why there is no sound when i unplug and then plug my speakers back in there is no sound. it just stops working completely, and the little speaker icon dissapears. i know the issue probably has something to do with me unplugging them while my computer was on, for some reason ubuntu 9.04 doesn't like that. theres got to be something that fixes it. oh and i have rebooted many times still nothing.

---

### Post by tommyss4l on 2010-03-29
Try going to System>Preferences>Sound that should get you all the options, if something is wrong that will hopefully give you the easy fix

---

### Post by tetsuo2010 on 2010-03-30
Everything looks good there under pref.  .....i was thinking maybe there's some sort of autodetect that ALSA has, and after unplugging them it doesn't see the sound. i even tried uninstalling and reinstalling ALSA and Pulseaudio, and ive seen that fix a lot of things for poeple, but still no sound. i thought it was wiered that you can kill pulseaudio in system tasks but there is no command to just start it up again, i have to reboot to restart it. also, i use wine and everytime i leave a wine program that had sound,...i have to reboot because wine seems to have stolen the sound and wont give it back to ubuntu for other uses. this might be related.

---

