---
title: "Realtek ALC662 Rev 1 - No Sound after Upgrade"
date: 2012-05-13
forum: General Help
---

### Post by mykrob on 2012-05-13
Our home computer was running Ubuntu 11.10, and it was working well. I upgraded to 12.04, and the performance boost is impressive, however, we now have no sound. I have gone through some troubleshooting steps to specify snd-hda-intel models, but to no avail. 

How does the sound just stop working after an upgrade? Was a kernel module left out?

At any rate, if anyone has some solution for this, it'd be greatly appreciated. My son uses LMMS to make his music and is greatly missing sound.

Thanks,
-myk

---

### Post by mykrob on 2012-05-14
Bump.

---

### Post by mykrob on 2012-05-25
back from vacation and still no responses. Anybody?

---

### Post by mcneely.mike on 2012-05-31
Just so's you know's, you're not alone... i just upgraded my kernel (as well as some other things that i was too tired to take notice of) and my sound has stopped as well.

Best i can find is a module WAS left out in the kernel upgrade 

(aplay -l aplay: device_list:252: **no soundcards** found...)

(lspci | grep Audio 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02))

The audio device is found, but i have no soundcard?!???

If i get time, i'm going to go look at the kernel to see what is going on.... have not recompiled a kernel in a loooooong time (about 10 years now), so will have to look up how to do it now.
Teach me to watch what is happening during an upgrade!

But yes, best i can tell it happened after the kernel upgrade.

---

### Post by mykrob on 2012-05-31
I ended up just buying an inexpensive soundcard. That seemed to be a quicker option.

Thanks for the reply, though. How do things like this even happen? Particularly after all the various kernel updates and such.

---

### Post by mcneely.mike on 2012-05-31
> **mykrob said:**
> I ended up just buying an inexpensive soundcard. That seemed to be a quicker option.

Thanks for the reply, though. How do things like this even happen? Particularly after all the various kernel updates and such.


I'm just curious as HECK now as to whether it was a sound module or what... and like i said, haven't recompiled a kernel in sooo long that i'm curious as to how things have changed in how to do it!  also, i'm on a small acer aspire so a new sound card isn't an option  :-(

Probably on another upgrade, your old sound card would come back, who knows.

;-)  Our avatars are fairly unusual, Hey, Hey, Hey!

Will try to post back here if recompiling works... using the directions on:

[https://help.ubuntu.com/community/AsusZenbook#How_to_recompile_kernel_for_Ubuntu_12.04_LTS_and_ux31e](https://help.ubuntu.com/community/AsusZenbook#How_to_recompile_kernel_for_Ubuntu_12.04_LTS_and_ux31e)

except i'm not doing the bluetooth patch

AND YOU ALSO HAVE TO 
apt-get install kernel-package
or the 
fakeroot make-kpkg clean
step will fail.


Okay, kernel rebuild failed... i think it will be more sane to just reinstall, due to the PPA's i have added and unwatched upgrades i have done.

Sorry... that's all i've got with so little time.

---

