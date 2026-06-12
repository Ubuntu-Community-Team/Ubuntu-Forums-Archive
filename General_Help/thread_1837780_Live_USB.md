---
title: "Live USB"
date: 2011-09-02
forum: General Help
---

### Post by CambridgePenguin on 2011-09-02
If I create a live USB with persistence then
presumably I can install packages on it and they will be preserved
as part of the system?

---

### Post by CambridgePenguin on 2011-09-02
I am mainly worried by this which I found on a fedora wiki:

========================
**Limited Lifetime of Persistent Overlay **
One very important  note about using the "primary" persistent overlay for system changes is  that due to the way it's currently implemented (as a LVM copy-on-write  snapshot), every single change to it (writes AND deletes) subtracts from  its free space, so it will eventually be "used up" and your USB stick  will no longer boot. Because of these limitations, it is advisable to  use the system-level persistence sparingly, for configuration changes  and important security updates only. For a truly persistent write-many  (vs write-once) overlay, use the *--home-size-mb* option to create a  home directory filesystem image for personal files. Unlike the primary  system overlay image, the home.img can be re-used and loop mounted  outside of the liveusb environment.
========================

Does this apply in Ubuntu also?

---

### Post by C.S.Cameron on 2011-09-02
That is how Fedora does it, not Ubuntu.
Ubuntu (persistent) stores stuff either in a file named casper-rw or in a partition of the same name. you can modify either.

---

### Post by garvinrick4 on 2011-09-02
> **CambridgePenguin said:**
> If I create a live USB with persistence then
presumably I can install packages on it and they will be preserved
as part of the system? Yes up to a 4 gig limit, a fat thing.
If you watch it being made in startup disk creator you will see in a 4 gig drive that it has 3.8 or so total
and when you give it persistence it will have a 3.1 gig persistence made. The first .7 gig for the .iso file
and the 3,1 gig for persistence. When you use install tool it will still install the original .iso file not the persistence. 
They do have DVD downloads that have .iso files that have up to 4 gig included in
the .iso file that will be installed using install tool on DVD.

---

### Post by CambridgePenguin on 2011-09-03
> **C.S.Cameron said:**
> That is how Fedora does it, not Ubuntu.
Ubuntu (persistent) stores stuff either in a file named casper-rw or in a partition of the same name. you can modify either.


Do you have a choice to use either a file or a partition?

I am creating USB live drives for a class and I want students to be able to write C code and compile/run it in the "data" part of the drive.

---

