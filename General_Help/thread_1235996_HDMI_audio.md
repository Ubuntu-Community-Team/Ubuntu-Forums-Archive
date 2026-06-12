---
title: "HDMI audio"
date: 2009-08-09
forum: General Help
---

### Post by beanverd on 2009-08-09
Newby here with a question.

I've spent the last week fighting my computer to get audio through HDMI with an ATI card working. I've found several tutorials online and this is what I can tell you:

System>preferences>sounds: I've set all of these to HDMI audio and I DO get sounds when I hit the test buttons.

In Volume Control I have enabled IEC958.

I have the latest drivers from ATI according to Hardware Drivers.

The weird thing is that I am getting audio. I can hear the test tones in sound preferences, and if I open a video in VLC (after tweaking setting there) I get perfect audio with my video. Songbird plays my MP3s perfectly and everything seems to be fine there.

I am not, however, getting system sounds, startup sounds, and more importantly, no internet audio works. This computer is used primarily as entertainment. We watch movies, listen to music, and surf the internet with it. Firefox will not give me audio for youtube videos (or any videos for that matter) lala.com will not work, pandora will not work. I can't help but feeling like I am just missing something simple somewhere along the road. Any advice anyone can give me would be great. Thanks!

---

### Post by beanverd on 2009-08-09
This is the result of   sudo lshw -c multimedia


  *-multimedia            
       description: Audio device
       product: RV620 Audio device [Radeon HD 34xx Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

