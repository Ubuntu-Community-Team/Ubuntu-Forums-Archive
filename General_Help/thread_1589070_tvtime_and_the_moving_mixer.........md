---
title: "tvtime and the moving mixer........"
date: 2010-10-05
forum: General Help
---

### Post by bowens44 on 2010-10-05
Ok , I migrated back from Maverick because I couldn't get Tvtime to work because /dev/mixer is no longer created in 10.10 so no volume control from within tvtime. I'm now back to 10.04.  

The issue that I'm having is that I have 4 devices that show up as /dev/mixer, /dev/mixer1,/dev/mixer2 and /dev/mixer3. I need to have tvtime use the mixer associated with my soundblaster audigy card. 

whenever I reboot, the order of these devices changes. Sometimes the soundblaster is assoaciated with /dev/mixer , sometimes it's /dev/mixer2 etc. 

Is there a way to ensure that the devices are always in the same place/order?

On a related note, sometimes my usb webcam is video1 other times it's video0 , this also causes problems with tvtime. 

How can I ensure that my system is the same after each boot?

I tried dev rules but couldn't get them to work properly.

any suggestions will be greatly appreciated.

thanks

---

### Post by rsarson on 2010-10-13
I've had the same problems as bowens44 - both the tvtime moving mixer problem and the video0/1 problem.

I also upgraded to Ubuntu 10.10 and noticed /dev/mixer is gone.  I've tried experimenting with all of the /dev/snd/ files with no luck.

Being able to control the volume directly in tvtime is an important feature and I hope someone can help us before I, too, have to downgrade to 10.04.

Thanks

---

### Post by alcarraz on 2010-10-18
same problem here but not the moving mixer part, just that in maverick tvtime doesn't let me change volume because it does not find the mixer.

any hints?

---

### Post by bowens44 on 2010-10-24
Finally solved all of my tvtime issues in maverick.

I got /dev/mixer back by compiling a custom kernel in which I enabled  the functionality that was turned off in 10.10.

The issue of the sound devices not always being initialized in the same order was :
[https://help.ubuntu.com/community/SoundTroubleshooting#Configuring](https://help.ubuntu.com/community/SoundTroubleshooting#Configuring) default soundcards / stopping soundcards from switching


Note: This section assumes that you have installed each soundcard properly.

In a shell, type cat /proc/asound/modules
This will give the the name and index of each soundcard you have currently. Make a note of the names, and decide which one you want to be the default card.
Now type sudo nano /etc/modprobe.d/alsa-base.conf
At the very end of the file, add the following (assuming you have 3 cards with module names A, B and C and you want to have them in the order CAB)

options snd-C index=0
options snd-A index=1
options snd-B index=2

---

