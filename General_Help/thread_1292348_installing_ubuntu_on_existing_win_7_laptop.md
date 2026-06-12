---
title: "installing ubuntu on existing win 7 laptop"
date: 2009-10-15
forum: General Help
---

### Post by fcuk112 on 2009-10-15
hi,

i have a laptop that is running win7 at the moment, i want to install ubuntu as well to do a bit of rails programming.  what is the best strategy with minimal work?  do i install via wubi or allocate some space to install ubuntu on another partition?  if the latter, how do i go about doing this?

thanks.

---

### Post by jbrown96 on 2009-10-15
Wubi would probably be the best method. 
You can also just install it along side. When you boot the LiveCD and choose to install, there should be an option to shrink the Windows 7 partition. That should work fine, but remember that resizing partitions is inherently risky, so make sure to backup your important data first.

---

### Post by fcuk112 on 2009-10-15
thanks - how is a wubi install different from a standalone ubuntu install?  i presume you still get all updates, can get any apps via sudo apt-get...?

---

### Post by Nburnes on 2009-10-15
> **fcuk112 said:**
> thanks - how is a wubi install different from a standalone ubuntu install?  i presume you still get all updates, can get any apps via sudo apt-get...?

Wubi creates a partition *inside* of Windows, so you don't get all the power benifits of having its own partition.

---

### Post by fcuk112 on 2009-10-15
to clarify, with wubi can i:

- sudo apt-get install apps
- get latest ubuntu updates
- run compiz (minor but nice)

just want to make sure i do the right thing installing wubi!  thanks!

---

### Post by fcuk112 on 2009-10-15
bump

---

### Post by raymondh on 2009-10-15
> **fcuk112 said:**
> to clarify, with wubi can i:

- sudo apt-get install apps
- get latest ubuntu updates
- run compiz (minor but nice)


Yes. However, I don't know how wubi relates well to win7.

I prefer to install ubuntu in it's own partition ... separating it from windows.  My main reason is that in a wubi-install, a windows crash also affects ubuntu.  Also, the state of Ubuntu depends on the "health" of windows.  Here's the wubiguide for your reference

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)  

If you have a capable enough machine, you can also consider virtualizing Ubuntu. Then again, it is also dependent on a healthy windows (as the host).

---

### Post by fcuk112 on 2009-10-16
> **raymondhenson said:**
> Yes. However, I don't know how wubi relates well to win7.

I prefer to install ubuntu in it's own partition ... separating it from windows.  My main reason is that in a wubi-install, a windows crash also affects ubuntu.  Also, the state of Ubuntu depends on the "health" of windows.  Here's the wubiguide for your reference

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)  

If you have a capable enough machine, you can also consider virtualizing Ubuntu. Then again, it is also dependent on a healthy windows (as the host).

thanks!  in the end i just resized my win7 partition and added an ext4 + swap, grub loader now allows me to switch between win7 and ubuntu upon boot.  relatively straightforward...

---

### Post by raymondh on 2009-10-16
> **fcuk112 said:**
> thanks!  in the end i just resized my win7 partition and added an ext4 + swap, grub loader now allows me to switch between win7 and ubuntu upon boot.  relatively straightforward...

Congratulations and happy ubuntu-ing :)

---

