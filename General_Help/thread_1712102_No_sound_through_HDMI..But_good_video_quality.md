---
title: "No sound through HDMI..But good video quality"
date: 2011-03-22
forum: General Help
---

### Post by schwabdale on 2011-03-22
I purchased a Nvidia card with an HDMI output. 
[http://www.nvidia.com/object/product_geforce_210_us.html](http://www.nvidia.com/object/product_geforce_210_us.html)

I installed the driver from System/Administration/Additional Drivers, 
When I hook it up to the tv (JVC) it gets the video no problem, but theres no sound. 
I told Ubuntu to use the HDMI output for sound..Nothing is muted...

Any help would be great,

Thanks

---

### Post by schwabdale on 2011-03-22
It looks like this is the same problem im having. Its confusing to me, can someone please break it down on how to fix this problem...Basically reword what they are saying the fix is

[http://ubuntuforums.org/showthread.php?t=1317408&page=1](http://ubuntuforums.org/showthread.php?t=1317408&page=1)


thanks

---

### Post by pqwoerituytrueiwoq on 2011-03-22
yuo could try nvidia's installer (it may work may not)
beware you will have to reinstall after ever kernel version update
it will also remove your current driver
must be installed via command line (GUI must be closed)
64bit driver
[http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html)
32bit driver
[http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html)

---

### Post by schwabdale on 2011-03-22
bump

---

### Post by ~Hinterland on 2011-03-22
Are you using Alsa or Pulseaudio? I'm asking because the other thread mentioned is 2yrs old.
If it's pulse the setting you want is on the Configuration tab > Profile.

(right click the volume icon > mixer)

---

### Post by schwabdale on 2011-03-22
Thanks for the reply. I am using alsa. I have not tried to disable anything through the bios yet.

---

### Post by schwabdale on 2011-03-23
Can anyone verify that a ATI Video card (ATi Radeon HD 5450)
Has no problems with ubuntu 10.10

---

### Post by antaios256 on 2011-03-23
im bumping this as I have recently discovered that with the last kernel update (may or may not be responsible) i have lost audio via HDMI - i use pulse audio(correctly configured) and sound just doesnt happen. i have installed all drivers for my video card using NVIDIA-Linux-x86_64-260.19.44 drivers (most up to date 1 week ago)

also running Ubuntu 10.10 on a DV7-3080ca
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01887277&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=4041789](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01887277&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=4041789)
(the link is to the laptop specs to make it a bit easier.)

---

### Post by schwabdale on 2011-03-23
What kern are you using?

---

### Post by antaios256 on 2011-03-23
> **schwabdale said:**
> What kern are you using?


i guess i kind of forgot to post that :P

```
uname -r
2.6.35-28-generic

```

---

### Post by schwabdale on 2011-03-23
Have you tried Rolling back?

---

### Post by adduds on 2011-03-23
I'm running an acer 5820TG 

HDMI video works fine aswell, the audio only comes through my laptop though...

toews@kidlapp:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC271X Digital [ALC271X Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

If i got to preferences --> sound

hardware i can only use the interal not the REDWOOD HDMI Audio [Radeon HD 5600 series]

i cannot disable my internal audio in bios as my bios does not offer that ability...this is most likely the issue?

anyone on this thread encounter this as i've noticed people have the same card

---

### Post by adduds on 2011-03-23
got it just had to set my audio to HDMI in sound options

---

### Post by antaios256 on 2011-03-23
> **schwabdale said:**
> Have you tried Rolling back?

i did a roll back 2 kernels and found that it just doesnt work . to verify that it wasn't a hardware issue i did boot into win7 and run HDMI to my TV audio works great (video quality on HDMI is better in ubuntu)  but yea so audio works on windows not linux.

---

### Post by Barry_IA on 2011-03-24
> **schwabdale said:**
> I purchased a Nvidia card with an HDMI output. 
[http://www.nvidia.com/object/product_geforce_210_us.html](http://www.nvidia.com/object/product_geforce_210_us.html)

I installed the driver from System/Administration/Additional Drivers, 
When I hook it up to the tv (JVC) it gets the video no problem, but theres no sound. 
I told Ubuntu to use the HDMI output for sound..Nothing is muted...

Any help would be great,

Thanks
[FONT=Palatino Linotype]

Schwabdale:

I just subscribed to your inquiry -- I'm having the same problems with at MSI R5450 video card (ATI Radeon) --or at least thinking they're similar.  If so, you might want to take a look at the solutions Nickrout gave me in my thread "Frontend Randomly Freezes" ([http://ubuntuforums.org/showthread.php?t=1675634](http://ubuntuforums.org/showthread.php?t=1675634)).

...Haven't figured out how to convert the fix there to the current problem. %)

-----

I found this which may be useful but I couldn't figure it out:  [http://www.mythtv.org/wiki/ATI_Radeon_HDMI](http://www.mythtv.org/wiki/ATI_Radeon_HDMI).  I couldn't figure out how to install the proprietary driver from Mythbuntu.

[/FONT]

---

### Post by Dumbestcrayon on 2011-05-12
I'm having the same issue and I can't figure it out. When I switch to HDMI in the sound preferences all flash playback in Google Chrome and Firefox is super speed.

---

### Post by Barry_IA on 2011-05-14
> **Dumbestcrayon said:**
> I'm having the same issue and I can't figure it out. When I switch to HDMI in the sound preferences all flash playback in Google Chrome and Firefox is super speed.

Hi Dumbestcrayon!

You might want to take a look at how I was helped to get my nVidia HDMI video card's sound working at:  [http://ubuntuforums.org/showthread.php?t=1675634](http://ubuntuforums.org/showthread.php?t=1675634).  And in case that's not quite right, look for "[solved] Frontend Randomly Freezes" by me (Barry_IA).  Towards the end is where NewLinux and others assist me in setting up my card to get sound.

Good Luck!  Let me know how things work out for you.

---

