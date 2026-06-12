---
title: "No sound"
date: 2009-10-15
forum: General Help
---

### Post by Alliance72 on 2009-10-15
Hello,

I've recently installed ubuntu 9.04 and for first couple of times everything was ok, but suddenly, after an update, my sound was gone. Here's what lspci showed me:
[http://www.paste.lt/paste/4a67386f24e6040ebb8d67a216120521](http://www.paste.lt/paste/4a67386f24e6040ebb8d67a216120521)


Has anyone got a solution? :/

---

### Post by jbrown96 on 2009-10-15
You probably just have a channel muted. If you right click on your volume control by the clock, there should be an option to open the mixer or something similar. This should give you access to several channels. There should also be a way to add additional channels. You are looking for channels like master, pcm, front, speaker, headphone. Play an audio file and mess around with the channels. If that doesn't work, I would recommend switching to ALSA. System-->preferences-->sound. Then change all the playback devices to ALSA. Reboot. Applications-->Accessories-->Terminal ```
alsamixer
``` Again go through the channels and unmute/turn them up. 
You don't want to have more channels unmuted than necessary, so when you find a configuration that works try to mute some of the unimportant ones (internal, mic, mic boost, etc.) and just leave the necessary ones turned on. Some extra channels may cause hissing, so you want them turned off.

---

### Post by Alliance72 on 2009-10-15
> **jbrown96 said:**
> You probably just have a channel muted. If you right click on your volume control by the clock, there should be an option to open the mixer or something similar. This should give you access to several channels. There should also be a way to add additional channels. You are looking for channels like master, pcm, front, speaker, headphone. Play an audio file and mess around with the channels. If that doesn't work, I would recommend switching to ALSA. System-->preferences-->sound. Then change all the playback devices to ALSA. Reboot. Applications-->Accessories-->Terminal ```
alsamixer
``` Again go through the channels and unmute/turn them up. 
You don't want to have more channels unmuted than necessary, so when you find a configuration that works try to mute some of the unimportant ones (internal, mic, mic boost, etc.) and just leave the necessary ones turned on. Some extra channels may cause hissing, so you want them turned off.

Thanks for your help, but he channels aren't muted (checked it a few times) and switching to ALSA didn't help :/ 

Any other ideas? :confused:

---

### Post by akakingess on 2009-10-15
Is it just the speakers, have you tried headphones to see if they even work, or are you getting absolutely nothing out of your machine?  I am not trying to be condescending, just want to clarify.

---

### Post by Alliance72 on 2009-10-15
> **akakingess said:**
> Is it just the speakers, have you tried headphones to see if they even work, or are you getting absolutely nothing out of your machine?  I am not trying to be condescending, just want to clarify.
Absolutely nothing from my machine.

But sound works in Windows XP...


Any ideas?

---

### Post by Alliance72 on 2009-10-15
Well, I've tried to search on google, but all I found is that one thread which says that Asus M2N68-VMsound** may** not work on linux.


So is this the end of the road? Should I uninstall ubuntu? :confused:

---

### Post by jbrown96 on 2009-10-15
Sound is notoriously complicated on linux. When I first got my laptop a couple years ago, I had to do a lot of work to get sound working. However, in later releases, it has worked without tweaking. I'm always hesistant to recommend beta software for new users, but that may be your best option. 9.10 comes out at the end of October. I haven't had any issues with it, so you may want to try it. The only downside is that there will be a lot of updates until it's released, which you may find annoying.

---

### Post by Alliance72 on 2009-10-18
> **jbrown96 said:**
> Sound is notoriously complicated on linux. When I first got my laptop a couple years ago, I had to do a lot of work to get sound working. However, in later releases, it has worked without tweaking. I'm always hesistant to recommend beta software for new users, but that may be your best option. 9.10 comes out at the end of October. I haven't had any issues with it, so you may want to try it. The only downside is that there will be a lot of updates until it's released, which you may find annoying.

Thank you! Well, I'll wait for the end of October :)

---

