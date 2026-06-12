---
title: "asus 1015pn overheating"
date: 2011-04-20
forum: General Help
---

### Post by imir on 2011-04-20
Hello,

I've recently bought the Asus 1015PN netbook with Windows 7 Starter pre-installed. It was running great until I decided to switch to Ubuntu netbook Remix. Running on Ubuntu, my netbook's cooling fans became much more noisy than on Windows, also the netbook is much more hotter at the bottom now on Ubuntu. 

I'v seen some other threads about overheating issues, but the solutions are for specific netbook models. I didn't find anything for my netbook. 

I am a new user of linux, so if I overlooked something simple, please direct me in the right direction.

---

### Post by Mark Phelps on 2011-04-20
At least you didn't come here demanding to know how to turn your fans down (and burn out your netbook in the process)!

My guess would be that Win7 supported CPU scaling and was cutting back on the CPU speed during idle times.  That would cause it to run cooler and keep the netbook cooler as well.

If the fans are running nearly all the time, your current kernel does not support CPU scaling such that it is running full-bore all the time, getting hot, and overheating your netbook.

Sorry ... don't have a solution ... but do have some advice:
1) Don't succumb to the temptation to turn your fans down.  They're running fast to keep the hardware cool.
2) If no one comes up with a solution soon, you will have a HARD decision to make -- as continuing to use the netbook while overheating is burning out the hardware.

---

### Post by imir on 2011-04-21
Thanks for the quick response Mark. I'm not sure why CPU scaling isn't working in ubuntu on my netbook... I will wait for a bit in case anybody else have something esle in mind, if not I guess I'll have to move back to windows.

---

### Post by anonymous777 on 2011-04-30
I have the same problem and i suspect ION. 

If i switch ION off and enable intel GPU then laptop seems to be cool. But with ION constantly running, CPU temp is rising up to 90C on flash playback, skype video calls and etc.

Hybrid graphics project doesn't look usable at the moment (i still have acpitools package i can't uninstall no matter what). If anyone have any ideas - i'd be glad to hear.

---

