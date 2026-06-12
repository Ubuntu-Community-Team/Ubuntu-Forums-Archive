---
title: "Touchpad driver other than Synaptics?"
date: 2009-07-15
forum: General Help
---

### Post by luken8r on 2009-07-15
Im trying to disable the touchpad on my HP laptop while typing and found quite a few appnotes/wikis on it regarding the Synaptics drivers. I installed gsynaptics and when I followed the directions from here

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

the terminal is telling me

luke@Laptop:~$ syndaemon
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
luke@Laptop:~$ 

I also tried the gui it installed and I got a similar error saying GSynaptics couldnt init, You have ot set SHMConfig to True oin xorg.conf

I go to xorg.conf and there is no entry for it

There is also no /etc/hal/fdi/policy/shmconfig.fdi

Is there another driver that I could use or something?

---

### Post by V_oron on 2009-09-23
**luken8r**, I have an identical problem in Ubuntu 9.04 on ASUS K40AB. And don`t have any ideas... :( Did you find the sulution?

---

