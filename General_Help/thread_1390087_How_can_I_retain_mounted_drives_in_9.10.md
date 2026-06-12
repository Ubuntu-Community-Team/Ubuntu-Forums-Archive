---
title: "How can I retain mounted drives in 9.10"
date: 2010-01-25
forum: General Help
---

### Post by cepost on 2010-01-25
I'm new to Ubuntu and was wondering if anyone knows how I can retain mounted volumes under my user ID. On my computer I have one IDE drive that is my boot drive and a mirrored SATA raid set. When I login as "root" and mount the SATA volume it's always there. When I logout or shutdown if I login as root it's always mounted. I want to do the same thing for my own user ID. I did a search on having volumes mounted when I boot but they seem related to older versions of Ubuntu. It almost seems like a permissions problem since the "root" ID mounts the volume when I boot and my user ID does not. Any help would be greatly appreciated.

---

### Post by warfacegod on 2010-01-25
Look into modifying your fstab.conf file for auto-mount.

---

### Post by cepost on 2010-01-25
When I did the search on this I saw that was the solution. But something just doesn't make sense to me ... why when I login as "root" and mount a drive it retains it? When I logoff or shutdown and log back in as "root" my mounted drives are there.
 
Why does "root" retain mounted drives and a normal user does not?

---

### Post by warfacegod on 2010-01-25
I think it has something to do with external drives. Linux may get cranky if an external is set to automount but isn't actually connected during boot up. Read again, the part where I said, "I think" because I'm giving you little more than my best educated guess.

Perhaps it does that in case another drive has, say, Windows on it. It would never do to have two OS's trying to boot at the same time. Again, a guess.

---

### Post by Grenage on 2010-01-25
> **cepost said:**
> When I did the search on this I saw that was the solution. But something just doesn't make sense to me ... why when I login as "root" and mount a drive it retains it? When I logoff or shutdown and log back in as "root" my mounted drives are there.
 
Why does "root" retain mounted drives and a normal user does not?

I would guess that perhaps fstab has the flag "nouser" associated with that drive's entry, you could try changing it to "user".

---

### Post by tcchris on 2010-01-25
there is a gui to do this without editing fstab directly .
Py something , cant remember the name

---

### Post by warfacegod on 2010-01-25
> **tcchris said:**
> there is a gui to do this without editing fstab directly .
Py something , cant remember the name

It's called pySDM and can be found in Synaptic. When installed, it will be in the Admin. menu as Storage Device Manager.

---

