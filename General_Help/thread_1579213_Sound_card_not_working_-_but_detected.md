---
title: "Sound card not working - but detected"
date: 2010-09-21
forum: General Help
---

### Post by theskipirate on 2010-09-21
Hi all,

First post so please be nice! Just converting over to ubuntu after using the scientific version of linux at university.

Anyway, everything now appears to be working and using the hardware drivers application I was able to install my wireless driver. However, there is no driver downloaded for the sound card by this way. I have followed the comprehensive sound problems guide on these forums [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and now I just need some extra help...(oh I have made under sound preferences that nothing is muted)

After typing aplay -l into a terminal I get the following output


**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


So I believe this shows the sound card is installed correctly. Then using alsamixer there is two channels I can change: master and PCM. Both are now at the highest setting and appear to not be muted.

I am fairly stuck from here. Any suggestions? I am using ubuntu 10.04

Thanks!

---

### Post by theskipirate on 2010-09-23
Bump - any ideas anyone?

---

### Post by mastablasta on 2010-09-23
the listed one looks to me more like graphics card with sound available.
 
anyway under sound preferences what kind of input output do you have selected? have you tried analog duplex (or at leats analog output)?
 
i am not quite sure but i think you should be able to change more than two channels on alsa-mixer :-O

---

### Post by lkjoel on 2010-09-24
> **theskipirate said:**
> Bump - any ideas anyone?
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by theskipirate on 2010-09-25
Thanks for the replies.

In the sound preferences I have for input: Internal Audio Analog Stereo. For the ouput: RS880 Audio Device Digital Stereo. There is also the option to change the output to  Internal Audio Analog Stereo

Will try fix your sound just now!

---

