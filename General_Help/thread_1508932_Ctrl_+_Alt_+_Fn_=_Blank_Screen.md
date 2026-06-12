---
title: "Ctrl + Alt + Fn = Blank Screen"
date: 2010-06-13
forum: General Help
---

### Post by VastOne on 2010-06-13
I cannot access xterm or an tty using ctrl alt fn getting just a blank screen.  Even in booting to repair mode or logging into Xterm, I get the same blank screen.

Lucid with nVidia X at 1900 x 1200 - Had this setup for the last year so Karmic and Jaunty had no issues with xterm

Needing to resolve this to be able to load nVidia drivers.

Thanks

---

### Post by efflandt on 2010-06-13
If using the default video drivers, did you try **nomodeset** kernel boot parameter?

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

When I had older nVidia on a laptop, I actually had no trouble until I installed nvidia(96) proprietary drivers.  I then got a totally blacked out screen (not even backlight) until in Screen section of xorg.conf added: Option "UseDisplayDevice" "DFP"

But I am not familiar with the blackout problem some have been having with fresh installations and default drivers.  I do know that when I tried enabling kms in 9.10 for my old ATI X1300, I had no Ctrl+Alt+Fn consoles.  That was not an issue for 10.04, but I had other issues with kms (which is now the default) that required **nomodeset**.

---

### Post by VastOne on 2010-06-13
> **efflandt said:**
> If using the default video drivers, did you try **nomodeset** kernel boot parameter?

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

When I had older nVidia on a laptop, I actually had no trouble until I installed nvidia(96) proprietary drivers.  I then got a totally blacked out screen (not even backlight) until in Screen section of xorg.conf added: Option "UseDisplayDevice" "DFP"

But I am not familiar with the blackout problem some have been having with fresh installations and default drivers.  I do know that when I tried enabling kms in 9.10 for my old ATI X1300, I had no Ctrl+Alt+Fn consoles.  That was not an issue for 10.04, but I had other issues with kms (which is now the default) that required **nomodeset**.

I appreciate the idea and info, this did not solve my issue.

---

### Post by VastOne on 2010-06-13
As a test, I booted into 2.6.35 rc3 which has no X support or video drivers, thus eliminating X from the equation and I still have the same problem.

---

