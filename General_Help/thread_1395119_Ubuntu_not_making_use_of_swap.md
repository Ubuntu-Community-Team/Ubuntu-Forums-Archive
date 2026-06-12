---
title: "Ubuntu not making use of swap"
date: 2010-01-31
forum: General Help
---

### Post by LinScape on 2010-01-31
When i installed Ubuntu on my computer, i noticed that the installer made a 1GB swap partition but Ubuntu does not automatically make use of it. Every time i start Gparted, it says that the swap partition is off. how do i make Ubuntu use the swap automatically on startup?

---

### Post by t4thfavor on 2010-01-31
sudo swapon -a

will turn all your swap on. I still doubt you will see much use of it.

---

### Post by philinux on 2010-01-31
> **LinScape said:**
> When i installed Ubuntu on my computer, i noticed that the installer made a 1GB swap partition but Ubuntu does not automatically make use of it. Every time i start Gparted, it says that the swap partition is off. how do i make Ubuntu use the swap automatically on startup?

Have a read. Should get you going. I have 2 gig ram and a 2 gig swap partition. The only time swap gets used is if I use a lot of virtualbox or hibernate the pc.

[https://help.ubuntu.com/community/SwapFaq#Why%20is%20my%20swap%20not%20being%20used?](https://help.ubuntu.com/community/SwapFaq#Why%20is%20my%20swap%20not%20being%20used?)

---

### Post by LinScape on 2010-01-31
So this means that Ubuntu will only make use of the swap partition only if its necessary?

---

### Post by The Cog on 2010-01-31
The command **swapon -s** will tell you if swapping is even enabled - it lists all the currently used swap partitions.

I have noticed that the Ubuntu installer configures fstab to reference the swap partition by UUID. The Ubuntu installer also reformats the swap partition if you install a second version of Ubuntu, thus changing the UUID of the swap partition and disabling swap on all other versions. 

Doh!

---

### Post by oldos2er on 2010-01-31
> **LinScape said:**
> So this means that Ubuntu will only make use of the swap partition only if its necessary?

Correct.

---

### Post by sandkernel on 2010-01-31
> **LinScape said:**
> So this means that Ubuntu will only make use of the swap partition only if its necessary?

Exactly - which is precisely what you want. Swap is just an extension of RAM and is used only when system resources get high enough that RAM is all but gone. Once this is done your pc will start using swap. Performance will be quite slow at this time - swap is on disk and is many times slower than RAM of course. The goal for a desktop system should be 0% swap used during **normal** circumstances. A server system may be able to function quite well with a small amount of swap usage.

---

### Post by mechro on 2010-01-31
> **The Cog said:**
> The command **swapon -s** will tell you if swapping is even enabled - it lists all the currently used swap partitions.

I have noticed that the Ubuntu installer configures fstab to reference the swap partition by UUID. The Ubuntu installer also reformats the swap partition if you install a second version of Ubuntu, thus changing the UUID of the swap partition and disabling swap on all other versions. 

Doh!

:shock: :shock: Thanks for the info. Have edited my jaunty fstab to /dev/.... instead of UUID.

---

### Post by LinScape on 2010-02-05
yeah and i also get this message at boot time referring to the swap partition but i dont understand it... ill try to write it down. (by the way thanks for all of your help)

---

