---
title: "Monitor problems on Lucid"
date: 2010-05-09
forum: General Help
---

### Post by The Switch Blade on 2010-05-09
Hi,

I have a new sony vaio VPCF11NFX/B with a fresh install of Lucid.

I am using a VGA-out to a LCD monitor. It shows up and is recognized. I cannot get video to appear on my laptop monitor. Moreover, when I unplug my external monitor, I cannot boot into ubuntu. It brings me to low graphics mode and I can't do anything from there because half of the screen is missing.

Thoughts?

---

### Post by Catharsis on 2010-05-09
Try booting with "nomodeset":
1) Hold Shift while booting.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to reboot.

Also, do you have the proprietary nVidia driver installed through System->Administration->Hardware Drivers?

---

### Post by The Switch Blade on 2010-05-09
I'll try that, and yes I do.

---

### Post by The Switch Blade on 2010-05-16
I can't get the shift thing to work. Also, I should mention that when I do go into low graphics mode, it looks absolutely awful. The top half of the screen is black with a white and black barcode looking thing covering half of it. Then the actual screen is split in half, with the right side on the left and the left side on the right.

---

### Post by Catharsis on 2010-05-16
Try removing the external monitor and then booting, holding down Shift while it comes up.

---

