---
title: "help! jaunty kernel panic/lock up and caps lock blinking"
date: 2009-08-23
forum: General Help
---

### Post by chersen on 2009-08-23
comp specs: hp dv6000 2gb ram 1.73ghz intel core duo jaunty 9.04

so ive been running a fresh install of jaunty for over a month now. still getting the hang of everything, so kind of new to it all. i recently was running my jaunty 2.6.28-15 and installed some updates (was having problems with that too) and maybe another app, but that was it. i pressed shut down and went to bed. when i woke, i saw that my comp actually hadn't shut down but paused on my desktop background all night. 

now, i cant even get passed grub. as soon as i select my kernel (2.6.28-15) or 2.6.28-14, 2.6.28-13, or 2.6.28-11, it gets to the ubuntu screen and the loading bar locks and the caps light blinks. when loading any of the recovery modes they say *"Kernel Panic - not syncing: Attempted to kill init!"*

tried doing research as how to fix a kernel panic or anything but not really helping since i cant even get into my system to do** sudo apt-get install linux-backports-modules-jaunty**. right now i am running off my livecd ok but i need to fix this problem. any suggestions? should i go to an older/newer kernel or can i repair those kernels that i have through my livecd of jaunty somehow?

thanks!

---

### Post by yoursdhansh on 2009-11-05
I have the same problem in my HP laptop dv2718us. kernel panic and ubuntu freezes while booting.  I did fsck for hard disk and it screwed the OS. Please help.

---

### Post by chersen on 2009-11-05
Hey...sorry but when I had this problem a while back I couldn't find any solutions. Everyone suggested different things that didn't work, so I ended up booting from my livecd and backing up all my data and reinstalling ubuntu. I know its not the answer you wanted to hear, but if you just go ahead with it now, it will save you a lot of time and anguish spent researching it. Trust me, there isnt much out there to fix it. Good luck!

(btw, if you can't access some of your files or can't copy them to back up, open a terminal and type gksudo nautilus and you can access everything through that)

---

