---
title: "Installing to Different Directory help"
date: 2010-05-28
forum: General Help
---

### Post by westicles on 2010-05-28
I am running ubuntu 10.04 off a live usb (Persistent Install)
and i was wondering if i could change where everything installs, for example 'Ubuntu Software Centre', as i have created a partition on my Hard Drive for ubuntu programs.

I have heard that if i move /home to the new partition it might do that, can anyone help me?
Thank you in advance

---

### Post by zvacet on 2010-05-28
If you make separate home partition then you will have your personal files and settings on it,but not installed packages.They are by default stored in var/cache/apt/archives.Making separate home you will give OS space on root partition (~ 10GB is enough I think but you can make it bigger if you want to).Give a rest of free space to home partition (except few GB for swap) and I think you will have enuogh space to install & run what ever you want.

---

