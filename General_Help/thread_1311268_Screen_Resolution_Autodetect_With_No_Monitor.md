---
title: "Screen Resolution Autodetect With No Monitor"
date: 2009-11-02
forum: General Help
---

### Post by onering on 2009-11-02
I'm using Ubuntu 9.10 but this issues has been with me since I started using Ubuntu 6.10.

I'm using a KVM (Keyboard, Video and Mouse) on two Ubuntu machines.  This allows me to use the same Keyboard, Monitor and Mouse for both machines.

If I boot Ubuntu Machine #1 while the KVM is switched over to the Ubuntu Machine #2, Ubuntu Machine #1 can't see the monitor and sets the screen resolution to 800x600.  There are no other higher resolutions available.

Is there a way to "hard code" Ubuntu to always boot at 1280x1024 regardless if there is a monitor present?  Or perhaps a way to ask Ubuntu to re-autodetect the monitor and resolution?

Thanks.

---

### Post by nikgare on 2009-11-02
This is a common fault with cheaper kvms - I have one of those too!

What you need to do is create an xorg.conf file and fill it with the correct information about your monitor.
You can get more info here:
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

---

