---
title: "Strange Boot Sequence?"
date: 2010-05-01
forum: General Help
---

### Post by techunit on 2010-05-01
Ok So I dual booted my system no problem and It is all working fine... Installed restricted drivers... Everything working

Here is my problem. After choosing ubuntu I get a blinking curser (looks like "_") for 10 seconds then a low resolution boot splash(dots going back and forth).

I haven't faced this problem for a while I remember fixing it in the past but I can't remember how. How can I get the high resolution boot splash. What can I do about the curser (looks like "_").

I hope this was clear.

---

### Post by WorMzy on 2010-05-01
Have you got a nVidia graphics card, and have you installed the propriety drivers for it?

Because Plymouth (the new boot splash program for Lucid) doesn't play well with nVidia propriety drivers, and AFAIK, there's no solution for this. (Aside from uninstalling the propriety drivers.)

---

### Post by Kilz on 2010-05-01
[Let me google that for you.]("http://lmgtfy.com/?q=lucid+boot+splash+reolution")

---

### Post by techunit on 2010-05-01
No I have ATI...

Another issue to bring up... Ubuntu doesn't resume from suspend either.

---

### Post by techunit on 2010-05-01
Well Even Though I don't have Nvidia Graphics the drivers were the culprit. Solved

---

### Post by techunit on 2010-05-01
Oh and the 10 seconds of the blinking curser (looks like "_")

---

### Post by BrokeMahPC on 2010-05-01
Let me guess - you had installed the ATI proprietary fglrx driver?
Does not play well with KMS and Plymouth - same thing happened to me.

---

### Post by techunit on 2010-05-01
I guest thats it

---

### Post by techunit on 2010-05-01
Anything on that blinking curser?

---

### Post by GSF1200S on 2010-05-01
> **Kilz said:**
> [Let me google that for you.]("http://lmgtfy.com/?q=lucid+boot+splash+reolution")

You misspelled resolution.

---

### Post by techunit on 2010-05-01
everyone knows that coders can't spell...

---

### Post by techunit on 2010-05-01
> **GSF1200S said:**
> You misspelled resolution.

I hate google! You can't find crap... Not to mention that we already figured that one out! What about the 10 seconds of flashing curser(looks like "_")

---

### Post by GSF1200S on 2010-05-01
> **techunit said:**
> everyone knows that coders can't spell...

Haha, just a little playful jab for Killz.

In short techunit, many people are having issues with Plymouth right now. Hopefully the Ubuntu devs will get all the bugs sorted with updates shortly in the future. Be thankful your system boots, as some people (myself included) had a nightmare getting 10.04 to do so. Im trying to figure out a solution to this as well (mainly for others- I disable all splash and prefer to see what the kernel is doing on boot), and I will post here if I figure out anything.

---

### Post by techunit on 2010-05-01
Thats ok everybody gets cranky wgen a new release comes out becuase everyone is searching to fix to there simple questions...Thanks alot for the help

---

### Post by BrokeMahPC on 2010-05-02
You need to purge / uninstall the fglrx driver and go back to using the default radeon driver if you want a nice looking Plymouth and no blinking cursors. This may cause other problems eg. the radeon driver runs hotter - causes problems for some laptops.
Problem: Need to purge -fglrx
Typically, the following manual commands will properly uninstall -fglrx:
```
    sudo apt-get remove --purge xorg-driver-fglrx
    sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
    sudo dpkg-reconfigure xserver-xorg
```
If you want desktop effects (compiz or KDE) you'll need the glx module loaded. This
will not work even after purging fglrx since a hanging libglx.so file is left around.
Both fglrx and xserver-xorg-core provide this file so to replace it with the correct
version you'll need to reinstall xserver-xorg-core as well.
```
     sudo apt-get install --reinstall xserver-xorg-core
```

I still had a problem with teh Plymouth splash not showing at boot - you need to get the frambuffer to use a higher res with:
```
 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
```
```
 sudo update-initramfs -u
```

---

### Post by techunit on 2010-05-02
Ok I will give this a try thanks

---

### Post by techunit on 2010-05-02
> **BrokeMahPC said:**
> I still had a problem with the Plymouth splash not showing at boot - you need to get the frambuffer to use a higher res with:
```
 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
``````
 sudo update-initramfs -u
```

Ok I get a blinking curser (looks like "_") and then a instant of the boot splash then log-in.
Is this what you meant? Or will the codes about fix the issue above. I completed the codes listed before the ones in this post but I am curious about whether you completely understood what I meant. Thanks for the help! :)

---

### Post by techunit on 2010-05-02
Note to: BrokeMahPC
Alright figured I got to have faith in the people helping me or there not going to keep helping me. What you posted worked marvelously reducing the number of curser blinks to 3 from 30. Thanks a ton.
Note to: Everybody else. Thanks at ton for your suggestions. I have never really had many problems with Linux in the past year, but I am often a late adopter of the latest release.

---

### Post by BrokeMahPC on 2010-05-02
Well it now sounds like it's working as good as it can! I think we were all expecting too much from Plymouth - lets see what happens in the next 3 - 6 months.

---

### Post by techunit on 2010-05-02
well yeah apparrently there were alot problems That I only encountered because of the ATI driver thanks alot for the help.

---

