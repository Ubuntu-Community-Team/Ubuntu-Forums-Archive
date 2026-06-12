---
title: "updates messed up my sound again"
date: 2010-12-05
forum: General Help
---

### Post by mastablasta on 2010-12-05
Updates overwrote my upgraded alsa (in 10.04) necessary for the sound card to work. i disabled the upgrades for sound but it seems that kernel update doesn't respect my wishes.

i am fed up with keep reinstalling same thing over and over again. i mean what kind of operating system overwrites higher drivers verison on security update?!?

i have a quesiton:

What ALSA version is in Ubuntu 10.10? 

Somehow informaiton i found online is kind of vague.

I would upgrade from LTS version if this would resolve my sound issues. i need alsa 1.0.23 for the things to work propperly.

---

### Post by mastablasta on 2010-12-06
I was checking the distrowatch and it says Ubuntu 10.10 uses Alsa 1.0.23. is this true?

---

### Post by 101011010010 on 2010-12-06
Hello.
I just checked Synaptic (in 10.10) and it shows that I'm using Alsa-base 1.0.23+dsfg-1ubuntu4.
If you want to keep on using 10.04, when you install the package you require, open Synaptic, highlight the package (in this case Alsa-base) and if you select the Package option, in the Menu Bar, you will see the option to "Lock Version". This should stop the package from being updated in the future.
I hope this helps.

---

### Post by mastablasta on 2010-12-07
ok thanks for the information.
 
actually my brother already did this in synaptic, but updates still overwrote the settings. maybe it was my fault as i deleted windows from the other partition and then updated grub. but i don't really see what grub has to do with this alsa, and where he got the old files (upgrade process as i understand removes them and also takes quite a while to complete).

---

### Post by 101011010010 on 2010-12-07
Hello again.
I wonder if a security update will override this setting. Just a thought.
Anyway I was reading a Debian How to, which started explaining how to "pin" an application so that it won't update. Ubuntu still seems to be able to do this using the /etc/apt/preferences file.
I'm not sure if pinning still works but it might be worth a try. 
I found an article about "pinning the kernel to prevent an update" and thought it might help.

[http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/](http://www.howtogeek.com/howto/10606/how-to-hide-kernel-updates-in-ubuntu/)

I'll be having a look at this later because it looks like something that may come in handy to know.
I hope this helps.
A.

---

