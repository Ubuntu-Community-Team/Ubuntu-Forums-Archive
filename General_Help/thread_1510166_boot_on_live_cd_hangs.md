---
title: "boot on live cd hangs"
date: 2010-06-15
forum: General Help
---

### Post by Krux 01 on 2010-06-15
ok. i have tried everything to install ubuntu 10.04 ....i used wubi and it hangs on boot...ive written an iso, and it still hangs...

i turn on. it says boot from cd. 

the keyboard=human screen comes up then goes black

nice looking ubuntu splash with scrolling dots appear. after about a Minuit it hangs and the dots stop scrolling....no keyboard commands work

ive tried to go into the keyboard=human screen by pressing a key

ive tried all different options in the f6 and f4 options

ive done all different cmos settings

what am i doing wrong 

my system is:
intel celeron 
2.66ghz cpu
496 mb of ram
graffics card is a sis 650/651/740/661fx/741/760 series with 16mb

---

### Post by bruno9779 on 2010-06-15
I think that your graphic card i below the minimum requirements for the normal install disk

You will probably succeed using the alternate install disk (alternate download options on Ubuntu main site)

---

### Post by Karjix on 2010-06-15
Well i have some kind of problem also.
Running an I5 2.66Quad Core With windows 7
ATI Radeon 5750
4096MB 1333Mhz RAM
 
Installation just freeze when im done chosing my keboard setup and on my way
from Step 3 to step 4 waited like 2 hours and nothing happend. Tried installing from USB /CD / DVD And from the Live Demo mode and still same thing happends.
 
I have 500GB HDD with Windows 7 
and a 148GB Disk thats for the Ubuntu 10.04
 
And i have done all steps in the menu that appers when you boot the disk and choose
keyboard mode.
 
Would love to know whats the trick here and sorry if i post in wrong forum.

---

### Post by Krux 01 on 2010-06-15
ok ...i am running a 32 bit system ... do i download the amd64 version? or another

---

### Post by Krux 01 on 2010-06-15
I think that your graphic card i below the minimum requirements for the normal install disk

You will probably succeed using the alternate install disk (alternate download options on Ubuntu main site)[/QUOTE]



by the way....i like ur avatar.....ha

---

### Post by Krux 01 on 2010-06-15
ok...i  installed the alternate version and when i chose to boot it a single blinking underline appeared then the screen went black and nothing happened for an hour.....

---

### Post by eggdeng on 2010-06-15
This (the original problem) sounds like the KMS bug. 
To install from live CD:
Hit the spacebar once you see the keyboard and stick figure, choose Try ubuntu without installing and hit F6 to edit the boot command. Add the arguments
```
i915.modeset=0 xforcevesa
```
and continue installation from the desktop icon.
To boot after installing
Press and hold down shift on boot (if necessary) to get to a boot menu, then press e to edit and replace 'quiet splash' with 'nomodeset'.
To make the setting permanent, choose from the options explained in the Release Notes [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes").

---

### Post by Krux 01 on 2010-06-16
ok i did this and i get the black screen with the scrolling white text ..... it pauses on stdin error... then goes on and then stops at ureadahead then says 10** terminated..... it wont even boot off the disk without installing

---

