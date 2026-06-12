---
title: "Need help!!!!!"
date: 2010-06-15
forum: General Help
---

### Post by ibe2fly4chu on 2010-06-15
I was trying to get my audio working over hdmi so i installed the nvidia 9 series latest video drivers. Long story short, it didnt have any effect. However while useing this driver, i noticed spikes in the cpu after trying to stream or play just about any video content. I uninstalled the driver and now i want to go back to the ubuntu recomended drivers (ones you get from system>administrator>hardware ) but everytime i try to install them via administrator>hardware it cannot find any drivers at all to recommend. I need drivers ubuntu recomended drivers for a nvidia 9400GT. Is there any way i can get ubuntu to give me those drivers again?

---

### Post by spotted zebra on 2010-06-15
well you can start here: [http://ubuntuforums.org/showthread.php?t=971317](http://ubuntuforums.org/showthread.php?t=971317)

they reference a slightly older version of ubuntu but the commands should be the same.

you could also try this: [https://answers.launchpad.net/ubuntu/+source/nvidia-common/+question/65765](https://answers.launchpad.net/ubuntu/+source/nvidia-common/+question/65765)

sorry i am just posting links but i would try these two if i was dealing with these problems myself. all i did was google "ubuntu drivers 9400gt".

it seems like the answer lies in loading some drivers from the synaptic manager.

---

### Post by ibe2fly4chu on 2010-06-15
a bit of effort but it solved it. not sure if its working correctly but at least i got the old driver back. Simply go to synaptic and  do a search for nvidia...install core drivers from there. after that i ran sudo nvidia-xconfig see if anything happend and at first it gave me some errors. I went to etc/x11/ and deleted all the back up .conf files (dont recommend you do this i was just guessing at this point.)...lol went back to terminal and ran "sudo nvidia-xconfig" again...and it made some new .conf files xD...restarted...and drivers seem to be working. Now i have to test it via steaming to make sure all my cores are not at 80% like before. 

Thanks a bunch.

---

### Post by spotted zebra on 2010-06-15
yea no prob. again sorry about the linking but it was better than nothing and i know that i didn't know enough to help you trouble shoot directly. i will have to remember this one for future reference. so thanks to you to for helping me learn something indirectly.

---

