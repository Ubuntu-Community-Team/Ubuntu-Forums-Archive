---
title: "Ubuntu on Studio 1555...Lots of issues."
date: 2009-08-18
forum: General Help
---

### Post by Tipoo on 2009-08-18
I recently installed Ubuntu on my new laptop, and mostly everything is going fine. My most major concern at first was the lack of audio, but i fixed that by changing some modprobe stuff. 

With that fixed i have been pretty happy with the installation, but there are still a few things that collectively are starting to annoy me. 


For starters, the brightness buttons dont work. Well, they do if i play with them right when Ubuntu starts, but they stop working a few minutes in. 

Secondly, windows are pretty laggy, which they shouldnt be on a system like mine (2.1GHz Core 2 Duo, 4GB RAM, Radeon mobile 4570 512mb). I suspect the culprit is the Catalyst video card drivers for the Radeon card, they are whatever the Update Manager downloaded for me and i suspect they aren't specific to my card. Anyone know of a better driver i could use?

Thirdly, opening up the screensaver settings and using it for even a few seconds causes a system crash, again i'm suspecting the video card driver but if you have any other thoughts on that please let me know. 

My fourth problem is that Ubuntu doesnt seem to know when its running on AC power and when its on battery, i.e the display doesnt dim to the setting that it should when on battery. The battery shows up when its supposed to (charging or discharging) but the rest of the system seems oblivious. 

And lastly, the system goes to sleep fine, but does not wake up (i have to shut it down manually and restart it). 


Help a brotha out y'all? I know i listed quite a few problems there but if you can help me solve even a few that would be fantastic. 

p.s i hope i put this in the right place, as a rule my first thread on any forum is in the wrong section :lolflag:

---

### Post by Tipoo on 2009-08-19
Deleted

---

### Post by Tipoo on 2009-08-23
bump

---

### Post by sandyd on 2009-08-23
> **Tipoo said:**
> I recently installed Ubuntu on my new laptop, and mostly everything is going fine. My most major concern at first was the lack of audio, but i fixed that by changing some modprobe stuff. 

With that fixed i have been pretty happy with the installation, but there are still a few things that collectively are starting to annoy me. 


For starters, the brightness buttons dont work. Well, they do if i play with them right when Ubuntu starts, but they stop working a few minutes in. 

Secondly, windows are pretty laggy, which they shouldnt be on a system like mine (2.1GHz Core 2 Duo, 4GB RAM, Radeon mobile 4570 512mb). I suspect the culprit is the Catalyst video card drivers for the Radeon card, they are whatever the Update Manager downloaded for me and i suspect they aren't specific to my card. Anyone know of a better driver i could use?

Thirdly, opening up the screensaver settings and using it for even a few seconds causes a system crash, again i'm suspecting the video card driver but if you have any other thoughts on that please let me know. 

My fourth problem is that Ubuntu doesnt seem to know when its running on AC power and when its on battery, i.e the display doesnt dim to the setting that it should when on battery. The battery shows up when its supposed to (charging or discharging) but the rest of the system seems oblivious. 

And lastly, the system goes to sleep fine, but does not wake up (i have to shut it down manually and restart it). 


Help a brotha out y'all? I know i listed quite a few problems there but if you can help me solve even a few that would be fantastic. 

p.s i hope i put this in the right place, as a rule my first thread on any forum is in the wrong section :lolflag:

yes. i have a better driver for you. ati drivers are a bit dodgy on linux. (their improving tho!), but perhaps you can try installing the drivers from
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

the second sounds like an acpi/powermanagement problem.

---

### Post by Tipoo on 2009-08-23
> **carlee said:**
> yes. i have a better driver for you. ati drivers are a bit dodgy on linux. (their improving tho!), but perhaps you can try installing the drivers from
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

the second sounds like an acpi/powermanagement problem.


Thanks for you help...I dont see the Radeon 4570 listed there though, if you look under Linux X86_64 and Mobile Radeon, it only shows cards from 4 generations back (the 1K series).

There is a Radeon 4550 listed under the regular Radeon section, but then wouldnt i loose the power saving benefits of the Radeon 4k series cards?

---

