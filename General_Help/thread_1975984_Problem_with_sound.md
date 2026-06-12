---
title: "Problem with sound"
date: 2012-05-08
forum: General Help
---

### Post by Oscar Rojas on 2012-05-08
I have some problems with sounds in Lubuntu 12.04. These are my first Linux experiences and I am not very familiarized with its details and terminology.
 
I am sure the hardware is OK because another Little distro (based on Debian) plays all sounds pretty good and the volume control tool is functional. 
 
But that is not the case with Lubuntu. There are no system sounds and applications like games generating sounds are silent too. 
 
The only sounds I can hear are from tunes played on line under Chrome (YouTube or similar)... but in those cases there is a weird behavior: the volume control in the on line application is working; but the volume control in the desktop does nothing, no volume change, no muting.
 
I have read about similar problems and the repliers suggested to install pulseaudio and pavucontrol. I did it but now the problem is worst: no sound from YouTube or any on line sound source.
 
I am attaching a System/Hardware Report. I hope you will discover the origin of my problem and may give me a solution.
 
Thanks.

---

### Post by Rodney9 on 2012-05-08
Lubuntu does not have System Sounds.

When you open pavucontrol make sure nothings muted and set your Intel Audio Device.

On older machines add-on tools for flash like these 2 can help - 

[https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/?src=api](https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/?src=api)

and 

[http://webgapps.org/add-ons/flash-aid/](http://webgapps.org/add-ons/flash-aid/)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Oscar Rojas on 2012-05-09
Thanks.
 
I discovered that right-clicking on the volume icon and then selecting volume control configuration was asking for pulseaudio or alsamixer. I installed both from via software center.
Playing with Alsamixergui I discovered a combination of buttons that allow me to control the volume. However the volume control at the desktop (the sliding vertical bar) was not operative.
Trying to access the volume control configuration this time I got a new error message asking to run manually start-pulseaudio-x11. I did it and now it said that pulseaudio is not installed (a bug in Software Center?) then I installed it from the terminal screen and now the volume control panel (the one for pavucontrol) is launched and every thing is right... but Alsamixer panel is now inoperative. Then I seems that pulseaudio takes control. So I installed alsamixer and everything is still fine. The sliding bar and the mute control are fully operative.
 
Really, I did not understand exactly the full process. But I fixed my problem and then I declare this thread SOLVED!

---

