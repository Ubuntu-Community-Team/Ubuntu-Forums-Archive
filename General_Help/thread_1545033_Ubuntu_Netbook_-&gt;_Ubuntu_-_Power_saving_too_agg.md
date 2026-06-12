---
title: "Ubuntu Netbook -&gt; Ubuntu - Power saving too aggressive"
date: 2010-08-03
forum: General Help
---

### Post by Chareos on 2010-08-03
Hi guys,

I moved from my Ubuntu Netbook install (9.10) to Ubuntu Desktop (10.4)

Now I'd like to act the sistem more like a desktop:
- HDD spinoff less frequent (My dream would be to have it trigger only by night)
- No black-screen as power saving (oabout this: I disabled any sort of screensaver, and in my custom xorg.conf there's no entry about powersaving).

How could I fix those annoyances ?


Thanks

---

### Post by Nostalos on 2010-08-03
Under the Systems | Preferences Menu  open up "Power Management"  

Can turn off hard disk spin down and display sleep for when on/off AC power.

---

### Post by Chareos on 2010-08-03
Thanks for your answer !

These settings have been on Never (and slow hdds unchecked) for long now, but still same problem.

There I guess it's something specific to ubuntu Netbook, perhaps some settings hidden in some config file... ?

---

### Post by Nostalos on 2010-08-03
You can check the Power Management savings on the hard drive with

"sudo hdparm -B /dev/sda" provided /dev/sda is the disk you are concerned with

should give you and output similar to 

/dev/sda:
 APM_level	= 254


and from the manpage
       -B     Query/set Advanced Power Management feature, if the  drive  sup&#8208;
              ports  it.  A  low value means aggressive power management and a
              high value means better performance.   Possible  settings  range
              from  values  1 through 127 (which permit spin-down), and values
              128 through 254 (which do not permit  spin-down).   The  highest
              degree  of power management is attained with a setting of 1, and
              the highest I/O performance with a setting of 254.  A  value  of
              255 tells hdparm to disable Advanced Power Management altogether
              on the drive (not all drives support disabling it, but most do).


Not sure on the video.

---

### Post by Chareos on 2010-08-03
Tried. "No supported" to everything.

My HDDs are 2 internals and 3 external (USB). All of them get aggressively powered off tough.

---

### Post by Nostalos on 2010-08-03
hrmm.  then I am not sure.  i will have to let someone with more experience with the matter respond.

---

