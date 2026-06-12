---
title: "Ubuntu 11.10 using Wubi"
date: 2012-04-19
forum: General Help
---

### Post by cgaie on 2012-04-19
I installed Ubuntu 11.10 last night using Wubi and it's really slow
and my Creative SB X-Fi Xtreme Audio doesn't work for playing music, the sound is all distorted and hopping

I can only hear only sound clicking on system/audio

Is that because Wubi?

Will I get better Ubuntu response is I install it on a partition alongside windows 7 than using Wubi?

Thanks

---

### Post by albandy on 2012-04-19
In this thread [http://ubuntuforums.org/showthread.php?t=1923547](http://ubuntuforums.org/showthread.php?t=1923547) explains how to fix your sound problems. Open a terminal and type this:


echo "echo options snd-hda-intel position_fix=1 model=3stack >> /etc/modprobe.d/alsa-base.conf" | sudo sh

then reboot the computer.

And yes, Ubuntu will work faster using its own partition.

---

### Post by tmaranets on 2012-04-19
Use Ubuntu on another partition, specifically for Ubuntu. I don't think your sound errors are caused by Wubi.

---

### Post by cgaie on 2012-04-19
> **albandy said:**
> In this thread [http://ubuntuforums.org/showthread.php?t=1923547](http://ubuntuforums.org/showthread.php?t=1923547) explains how to fix your sound problems. Open a terminal and type this:


echo "echo options snd-hda-intel position_fix=1 model=3stack >> /etc/modprobe.d/alsa-base.conf" | sudo sh

then reboot the computer.

And yes, Ubuntu will work faster using its own partition.





Typing echo "echo options snd-hda-intel position_fix=1 model=3stack >> /etc/modprobe.d/alsa-base.conf" | sudo sh

and hit enter doesn't do anything

---

### Post by albandy on 2012-04-19
> **cgaie said:**
> Typing echo "echo options snd-hda-intel position_fix=1 model=3stack >> /etc/modprobe.d/alsa-base.conf" | sudo sh

and hit enter doesn't do anything

See the atached image please.

---

### Post by Mark Phelps on 2012-04-19
> **cgaie said:**
> ... Is that because Wubi?...
NO -- Ubuntu is functionally identical, whether installed using Wubi or installed in its own partition.

> Will I get better Ubuntu response is I install it on a partition alongside windows 7 than using Wubi?
Two-part answer:
1) yes -- but it won't be enough to notice.  Running Ubuntu from a Wubi-based install has very little effect on it's performance.
2) Installing alongside Win7, especially if its done using the Installer to shrink the Win7 OS partition, runs the risk of corrupting the Win7 OS filesystem.  And if that happens, not only do you NOT have a working Ubuntu, you also do NOT have a working Win7.

---

### Post by cgaie on 2012-04-19
> **Mark Phelps said:**
> NO -- Ubuntu is functionally identical, whether installed using Wubi or installed in its own partition.


Two-part answer:
1) yes -- but it won't be enough to notice.  Running Ubuntu from a Wubi-based install has very little effect on it's performance.
2) Installing alongside Win7, especially if its done using the Installer to shrink the Win7 OS partition, runs the risk of corrupting the Win7 OS filesystem.  And if that happens, not only do you NOT have a working Ubuntu, you also do NOT have a working Win7.

Thanks for your answer because I was about to install it on another partition from the the installer going for the third option and selecting my empty partition

I think I will go back to wubi to see if I can sort the audio problem

I really like Ubuntu, tired of Windows ):P


Thanks

---

### Post by cgaie on 2012-04-19
> **albandy said:**
> See the atached image please.

Hi

The screenshot was very useful but still I don't have audio

Here are my commands result.

  	 	 	 	 	 	  xps8300@ubuntu:~$ tail -n 2 /etc/modprobe.d/alsa-base.conf  
 # Keep snd-usb-audio from beeing loaded as first soundcard  
 options snd-usb-audio index=-2  
 xps8300@ubuntu:~$ echo "echo options snd-hda-intel position_fix=1 model=3stack >> /etc/modprobe.d/alsa-base.conf" | sudo sh  
 [sudo] password for xps8300:  
 Sorry, try again.  
 [sudo] password for xps8300:  
 xps8300@ubuntu:~$ echo "echo options snd-hda-intel position_fix=1 model=3stack >> /etc/modprobe.d/alsa-base.conf" | sudo sh  
 xps8300@ubuntu:~$ tail -n 2 /etc/modprobe.d/alsa-base.conf  
 options snd-hda-intel position_fix=1 model=3stack  
 options snd-hda-intel position_fix=1 model=3stack  
 xps8300@ubuntu:~$
 

What else can we do?  Should I go to beta 12.04

What I don't understand is why if I go to system settings/audio and I test the speakers then I have audio
but if I play music I don't have audio

Thanks Gracias

---

