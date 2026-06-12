---
title: "Several versions of Ubuntu kernel in Grub2 boot menu - can I delete old ones?"
date: 2010-03-03
forum: General Help
---

### Post by InspironDualBoot on 2010-03-03
My Grub2 boot menu includes:

...
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
...

Q1) I only really need the latest kernel, 2.6.31-19, don't I?

Q2) So how can I get rid of the two 2.6.31-14 entries?

TIA

---

### Post by spiky001 on 2010-03-03
hi it is best to keep an old kernel, just incase something gose wrong with the current 1, they will allow you to get back into your system

---

### Post by halj32 on 2010-03-03
as above it's best to have 2 kernels
but if you want to remove the old one you can do it with "synaptic", just do a search for the old kernel & uninstall it (you can also remove the headers etc.)

---

### Post by timgood on 2010-03-03
Much easier to install Ubuntu Tweak from GetDeb as detailed in my post here:

[http://ubuntuforums.org/showthread.php?t=983613]("http://ubuntuforums.org/showthread.php?t=983613")

---

### Post by QLee on 2010-03-03
> **InspironDualBoot said:**
> My Grub2 boot menu includes:

...
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
...

Q1) I only really need the latest kernel, 2.6.31-19, don't I?

Q2) So how can I get rid of the two 2.6.31-14 entries?

TIA

I agree with the other poster, spiky001, that it's better to keep one version older, at least until you've made sure the new one works and there aren't any regressions that affect your system.

It's possible for root to edit the grub.cfg file so that those entries don't show but that will only persist until the next time grub update is run. For instance, next kernel upgrade. That may be what you choose to do. It's also possible to create "static" entries that you control but then you will have to watch things yourself, not rely on automagic. This stuff should only be attempted by advanced users who have a decent understanding of GRUB2.

---

### Post by InspironDualBoot on 2010-03-04
Thanks everybody, sage advice!
(and timgood, thanks for the link to the other thread - very helpful)
I won't delete anything just yet, but when I have too many kernel verisons I'll try the suggestions for removing older ones.
Thanks again

---

