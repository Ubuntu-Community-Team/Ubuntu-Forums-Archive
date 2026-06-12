---
title: "mouse briefly freezes when pressing keyboard key"
date: 2009-12-19
forum: General Help
---

### Post by m4lte on 2009-12-19
Hi there,
I'm experiencing a strange problem in Ubuntu 9.10. **When I move the mouse and at the same time press a key, the mouse cursor briefly freezes** and after approx. half a second continues to move. It makes a jump, suggesting that just the "image" of the cursor freezes, while the actual position is still updated.
Curiously this does not happen for modifier keys (e.g. ctrl, alt, shift, windows-key) and also it does not happen all the time but only for approximately every other key stroke.

Also I just reinstalled my system but kept my /home folder. The problem persists, so it must be linked to something going on in my /home directory.
Any ideas what could be the reason?

cheers!

**SOVLED:**
You can fix this by using gconf-editor and changing the value in
/-->desktop-->gnome-->peripherals-->touchpad-->disable_while_typing
to false.
see: [http://swiss.ubuntuforums.org/showpost.php?p=8337500&postcount=6](http://swiss.ubuntuforums.org/showpost.php?p=8337500&postcount=6)

---

### Post by m4lte on 2009-12-20
I just made a clean install of 9.10 on my Lenovo Thinkpad R400.
The mouse still gets "stuck" when I press a key. Is that normal? Does anyone notice the same?

---

### Post by SecretCode on 2009-12-20
Sounds like (and I'm only guessing here) a video driver problem. What's your video card?

---

### Post by m4lte on 2010-01-03
> **SecretCode said:**
> Sounds like (and I'm only guessing here) a video driver problem. What's your video card?

I have an Intel GMA X4500 MHD.

---

### Post by SecretCode on 2010-01-03
Does anything show in System > Administration > Hardware Drivers?

---

### Post by m4lte on 2010-01-04
> **SecretCode said:**
> Does anything show in System > Administration > Hardware Drivers?

Just says "No proprietary drivers are in use on this system"


I suppose I'm experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466288/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466288/)



**SOLVED!!** see my edit in the first post.

---

