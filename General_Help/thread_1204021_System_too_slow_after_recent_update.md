---
title: "System too slow after recent update"
date: 2009-07-04
forum: General Help
---

### Post by asamay81 on 2009-07-04
I am using a compaq presario SR 1630IL desktop, Pentium IV, 3.06 GHz, 1 GB RAM. I have ubuntu 9.04. Problem is that after i have installed the recent updates yesterday, the system is performing too slow :(. switching on to the older karnel did not help me. 


any help will be highly appreciated

thanks

---

### Post by earthpigg on 2009-07-04
open a terminal, and run top

keep that floating in the background, and keep your eye on what process has the highest %CPU usage.... once we find out what is slowing things down, we can go from there :)

for me, rhythmbox and firefox-3.5 are taking turns at that top spot, so that is what is slowing me down... but that is ok, since i am using both. if it was something im not using, or that doesn't make sense to be taking up so much processor, then that would be the problem and we could go from there.

---

### Post by lovinglinux on 2009-07-04
The culprit is probably the Remote Desktop. Disable it in "System >> Preferences >> Startup Applications (aka Session)".

For additional performance tips, check [this thread](http://ubuntuforums.org/showthread.php?t=1152095).

---

### Post by asamay81 on 2009-07-04
thanks a lot for the replies......disabling the remote desktop resumed my system performances...now it is satisfactory.....

thanks again :)

---

