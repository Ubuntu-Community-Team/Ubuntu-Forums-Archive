---
title: "Kernel upgrade, lost audio - help?"
date: 2010-05-09
forum: General Help
---

### Post by drhiii on 2010-05-09
System did an automatic upgrade including from kernel kernel 2.6.32-21-generic to kernel 2.6.32-22-generic.  Audio has disappeared.  There are not hardware choices in the Sound Preference/Hardware tab at all.  

I've seen this before, but cannot remember exactly how to go about rescuing from this condition other than editing grub to boot into the older kernel.

Help anyone, on how to restore audio with this upgraded kernel?

thank you

---

### Post by ibrahim.k on 2010-05-09
I think you should download the latest version of ALSA 
[B][*Advanced  Linux Sound Architecture*]("http://www.alsa-project.org/")

and chick [/B]
**[*alsamixer*]("http://www.alsa-project.org/")**


raise the volume

---

### Post by finlost on 2010-05-09
Check alsamixer

---

