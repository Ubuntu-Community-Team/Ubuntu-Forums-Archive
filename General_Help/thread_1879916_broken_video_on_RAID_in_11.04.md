---
title: "broken video on RAID in 11.04"
date: 2011-11-12
forum: General Help
---

### Post by kuritsubaji on 2011-11-12
Oh deary me!!!:oops::sad: I do believe I have haphazardly careened my system to a bit of a precipice and I am turning to the community to hopefully save it before I bosh it up any further and it tumbles over the edge into oblivion...
 
I wouldn't consider myself a complete noob, but more like: just experienced enough to get myself in trouble (obviously), so I'll explain as best I can, what I've done so far:

I'm running Ubuntu 11.04 64-bit (strictly, no dual boot or other OS) on a software RAID0 array (4x500MbSATA). This is in my own DIY box with a NVIDIA pair of GeForce GTS 250 video cards. In an attempt to resolve issues with a 3 monitor setup not switching between a 2D desktop on 3screens and a 'fullscreen' mode 3D application on 1screen without crashing the system (other issue entirely), I was about to reinstall the proprietary drivers and had removed the current (recommended), yet oddly not activated ones. After removal, I rebooted and was only able to get a purple screen with a big stripe of jumbled video garbage. Since I am running on a RAID array, and installed with the alt installer, a 'live CD' or BootRepair is not an option as I can't get the array to mount (yes, I already tried). Booting up with an 11.04 64-bit alt install USB stick will only get me as far as a being able to assemble the array, mount it and execute a shell (so, I know it's still there), but as much as I look, I can't seem to find any clear info on what is going to get my video drivers straightened out from this point. Running **apt-get update** yields the same "purple stripe-of doom" upon booting to the array.

Next move?

---

### Post by kuritsubaji on 2011-11-13
Seriously, my system has ground to a halt and I am at a loss as what to do next.

Do I need to provide more details? 

Is there a simple way to restore the video drivers from the rescue shell and I'm missing it?

Is there a file or script I need to post? 

Most problems and gaffs of the past have been easy to fix or get help on, but this one seems to be flapping in the breeze.

At worst, I would simply burn the /home folder to a few DVDs and rebuild the entire array, but that seems like overkill.

Please please please, stop me before I do something rash!

---

