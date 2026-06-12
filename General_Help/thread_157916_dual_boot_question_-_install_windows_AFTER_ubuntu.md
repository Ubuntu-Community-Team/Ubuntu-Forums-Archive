---
title: "dual boot question - install windows AFTER ubuntu"
date: 2006-04-10
forum: General Help
---

### Post by neoroses on 2006-04-10
okies i wana make a dvd with 6 tv eps on and the only easy way i kan do this is by using CONVERtXTODVD, wine does run this but bloody slowely n i krnt risk it messing up as i need it done fast. so the only way i kan think of doing this is re-installing windows on a small partition, however ubuntu is currently taking up all of my hdd space, is there a way i kan install windows and keep ubuntu or have i got to wipe...install windows and the put ubuntu back on setting up dual boot that way?

thanx

---

### Post by snufkin on 2006-04-10
It is possible to resize Linux partitions, but I've never had any luck with installing Windows second.  For a start, you'll need to set up the boot-loader again, and there are other probs I've run into.

You might have the best luck fitting a second hard drive and installing Windows onto that.  But remember you'll need a strategy for restoring the boot-loader afterwards...

---

### Post by neoroses on 2006-04-10
mokay thanks =)

---

### Post by justleen on 2006-04-10
i have had no problems with this whatso ever..
resize with gparted livecd, install windows and  restore grub afterwards (see sig)

---

