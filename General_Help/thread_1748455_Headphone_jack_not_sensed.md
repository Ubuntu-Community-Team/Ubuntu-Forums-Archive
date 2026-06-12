---
title: "Headphone jack not sensed"
date: 2011-05-03
forum: General Help
---

### Post by Simeo on 2011-05-03
Ok, I don't really understand this. I had Ubuntu 10.10 and everything worked. Then my hard drive crashed and I replaced it and reinstalled Ubuntu 10.10. After the re-install, my headphone jack is no longer sensed. It works when I boot the computer with the jack already in, but if I take it out after the boot it doesn't work. Also, Vica-Versa. If I don't have it in, it won't work when I put it in until a reboot. 

If I'm playing music through the internal laptop speakers and put the jack in the music will continue playing through the laptop speakers and not transfer. 

Very strange and never did this before. I thought the Ubuntu 11.04 update would fix, but didn't. I've tried to google all sorts of fixes and still no change. Help?

---

### Post by dino99 on 2011-05-03
watch the alsamixer settings

---

### Post by Simeo on 2011-05-03
Could you please be more specific?

---

### Post by Simeo on 2011-10-29
So after numerous issues with 11.10 on my computer, I reverted to 11.04LTS. Everything is (finally) working great...BUT I forgot about this issue I had with 11.04 and I don't remember how it was fixed...

Little help?

---

### Post by jorenl on 2012-08-23
I apologize for reviving this ancient thread, but the exact same issue affects me in Ubuntu 12.04 .

If  I boot with my headphones plugged into the line out jack, the internal  laptop speakers are disabled and I can use my headphones properly. If I  remove my headphones, there is no sound.

If I boot with my line  out jack empty, the laptop speakers keep activated, even after plugging  in my headphones. My headphones function normally, but the speakers  aren't deactivated.

I have tried changing about all settings in  alsamixer, but there does not seem to be a volume control that effects  either only the built-in speakers, or only the line out.

Here's my sound hardware info (using analog, not digital):
```
joren@herent-drie-ub:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Any help/tips to get me (and others experiencing the same problem) started on fixing this would be greatly appreciated :)

---

