---
title: "Help with monitor out of range?"
date: 2011-01-01
forum: General Help
---

### Post by trevy on 2011-01-01
Hey friends happy New Year. I need help i got an old monitor, and after the BIOS boots to load Ubuntu it says the monitor is out of range and to fix my PC setting. can someone tell me how to fix that?

---

### Post by dcstar on 2011-01-02
> **trevy said:**
> Hey friends happy New Year. I need help i got an old monitor, and after the BIOS boots to load Ubuntu it says the monitor is out of range and to fix my PC setting. can someone tell me how to fix that?

You have to boot into "safe" graphics mode and set things so the resolution you are using matches the monitor's capabilities.

---

### Post by cheapie on 2011-01-02
> **dcstar said:**
> You have to boot into "safe" graphics mode and set things so the resolution you are using matches the monitor's capabilities.

How to boot to safe graphics mode:

When (re)starting the computer, hold down the SHIFT key. The GRUB menu should appear. Using the arrow keys, navigate to a "Recovery Mode" option and press ENTER. At the next menu (should have a blue background), select "failsafeX" with the arrow keys and press ENTER. This should bring you to the failsafe graphics mode, and let you configure the X server automatically or manually.

---

### Post by cariboo on 2011-01-02
You neglected to say what type of graphics card you're using, as you may have to create an /etc/X11/xorg.conf file, and set the correct horizontal and vertical refresh rates by hand in order to get the proper resolution.

---

