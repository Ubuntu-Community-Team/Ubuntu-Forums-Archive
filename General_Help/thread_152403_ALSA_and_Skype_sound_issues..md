---
title: "ALSA and Skype sound issues."
date: 2006-03-29
forum: General Help
---

### Post by nuky on 2006-03-29
Hi, 
I'm having problems with my sound on Kubuntu, can anyone help? 

I followed the ALSA setup instructructions on the WIKI, to install libesd-alsa0 and set it up like they said.. Instructions are also here - [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063) 

I then installed skype_dsp_hijacker (through aptitude), as my Skype only allowed me to make one call at a time. 

However, now Skype only works on and off, and I still have to restart the ALSA sometimes. Furthermore, I can't hear ANY other sound on my pc, even when Skype isn't running!! 

When I try to change my Hardware setting in K -> Settings -> Sound & Multimedia -> Sound System, I get the following message:

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for capture (Invalid argument)
The sound server will continue, using the null output device.

This message appears whenever I try to change it to any of the options in the list (Autodetect, ALSA, ESD,...).

I'm still new to Linux and not sure what other information would be useful in diagnosing what's wrong here, but if you need any further information, PLEASE do not hesitate to ask. 

I have tried to uninstall the skype_dsp_hijacker, and undo the configurations in the ALSA settings on the WIKI, but still no luck in getting sound from other programs on my PC. I would basicaly, just like to get my regular PC sounds working again, like KAlarm, Amarok, etc.. at the moment. I do not even mind having to restart Skype again after each call!! Any help would be GREATLY appreciated! :o)

---

### Post by ozorba on 2006-03-30
Try this link. It worked on my pc.

[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

Cheers,
OZ

---

### Post by nuky on 2006-03-30
Hey, 
Thanks for the reply. After, playing about with it and the sound system settings, I'm not entirely sure what i did but now I have sound working with Skype running, but not when I'm a call. 
I think I forgot to create the link at the bottom of the page that you posted! 
Thanks again. :)

---

