---
title: "Can't boot text messages"
date: 2011-04-15
forum: General Help
---

### Post by troyguffey on 2011-04-15
I'd like to see the messages that Ubuntu can give while booting.  I've eliminated the "quiet splash" from the bootup, but now instead of the boot-up splash I get a totally blank screen. Ubuntu 10.04 with the -30 generic kernel.

---

### Post by lithopsian on 2011-04-15
Without splash, your boot should be a console rather than a framebuffer.  Although this should be a very basic thing that works on all graphics cards, the advent of things like KMS means that cards and kernels often try to do fancy stuff and you get nothing.

You could just turn on splash and leave quiet off.  You will get messages scrolling by under the logo, I think.  Worth a try anyway.

---

### Post by Hippytaff on 2011-04-15
This information can be found by doing```
dmesg | less
``` after boot

---

### Post by oldos2er on 2011-04-15
> **troyguffey said:**
> I'd like to see the messages that Ubuntu can give while booting.  I've eliminated the "quiet splash" from the bootup, but now instead of the boot-up splash I get a totally blank screen. Ubuntu 10.04 with the -30 generic kernel.

Put "text" in place of "quiet splash", then sudo update-grub.

---

### Post by Hippytaff on 2011-04-15
> **oldos2er said:**
> Put "text" in place of "quiet splash", then sudo update-grub.

well I never knew that - excellent - one for the notes :-)

---

