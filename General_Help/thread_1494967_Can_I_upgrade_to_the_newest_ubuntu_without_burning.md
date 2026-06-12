---
title: "Can I upgrade to the newest ubuntu without burning a cd??"
date: 2010-05-27
forum: General Help
---

### Post by alxpenguin on 2010-05-27
Hey so I would like to upgrade from Jaunty to the newest version. Do I have to do the whole burning of the ISO file unto a cd again? Or mount it from within? Is there a download command to just get the upgrade?

---

### Post by oleink on 2010-05-27
> **alxpenguin said:**
> Hey so I would like to upgrade from Jaunty to the newest version. Do I have to do the whole burning of the ISO file unto a cd again? Or mount it from within? Is there a download command to just get the upgrade?

I'm pretty sure you can only upgrade to Karmic then youd have to upgrade from there.  And you could use the update manager.

---

### Post by wojox on 2010-05-27
You would have to upgrade from 9.04 to 9.10 then 10.04. Better of just burning a new CD and doing a fresh install to take advantage of Grub2 and ext4 in my opinion. :)

---

### Post by oleink on 2010-05-27
> **wojox said:**
> You would have to upgrade from 9.04 to 9.10 then 10.04. Better off just burning a new CD and doing a fresh install to take advantage of Grub2 and ext4 in my opinion. :)

I do agree with this although if you don't want to you can use the update manager and move upgrade twice like he said from Jaunty->Karmic->Lucid.  But his suggestion is pretty solid.  I am going to do a fresh install every other release.

---

### Post by alxpenguin on 2010-05-30
Hmm ok what is the advantage of downloading and burning? What does taking advantage of Grub 2 Dev 4 mean?

---

### Post by DomesDKG on 2010-05-30
Grub was updated (the boot manager) and installing from the disk should update this as well.  All in all, it's good to do a clean install from time to time, because some files can get messed up after repeated upgrades, or just mistakes made over time.

The difference here in burning a cd vs using the update manager is the update manager just updates your existing system, while the cd lets you do a clean install.

---

### Post by jerenept on 2010-05-30
You can use a Live USB, if your BIOS allows booting from USB.

---

