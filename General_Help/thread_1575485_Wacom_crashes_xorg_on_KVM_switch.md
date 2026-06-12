---
title: "Wacom crashes xorg on KVM switch"
date: 2010-09-15
forum: General Help
---

### Post by yorkshirelandscape on 2010-09-15
When I switch my KVM over to my Ubuntu box, the Wacom tablet causes X to crash about 1 out of every 4 times. I will usually see what I'm supposed to for a split second, get a blank screen and/or command line for a second, then I'm back at the login screen.

Xorg.4.log: (EE) Wacom Graphire4 4x5: Error reading wacom device : No such device

If the tablet is plugged directly into the KVM, it crashes every time. Instead, I have the tablet plugged into my Mac laptop, which is itself plugged into the KVM (TrendNet USB w/audio, if it helps).

---

### Post by luecjennifer on 2010-09-21
There is a slight chance that your kvm switch has a some errors, though it would be better to contact the manufacturer.

---

### Post by luecjennifer on 2010-09-21
If nothing improves just google to find a new kvm switch

---

### Post by Inaimathi on 2011-01-28
Similar issue here; X crashes whenever I switch back to the Debian machine using my KVM.

I've found that if I don't have the pen/mouse in contact with the tablet surface, it doesn't crash X (but does consistently if a pointing device is touching the tablet). I've just gotten into the habit of using my pen holder when I'm switching.

---

