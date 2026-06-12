---
title: "Aspire One Netbook Powers Off By Itself After Update"
date: 2009-09-14
forum: General Help
---

### Post by gilester on 2009-09-14
Hi,

I'm using Jaunty (netbook reloaded version) on an Asus Aspire One netbook. Last weekend I did a system update, nothing strange there, I've done them before. But this time something has broken with the power control.

I noticed while the update was progressing that the little battery icon had changed to a grey one saying 'service unavailable' or similar, but I thought nothing of it, assuming after a reboot it would come back OK.

No such luck. Now whenever I boot the netbook it gets as far as the desktop environment, then turns straight off. It may be a coincidence, but it appears to turn off roughly at the time the power manager icon might be being loaded, although that could be a red herring.

I have tried with the power connected and running on battery, but the same result both times. Seeing as the machine never gets to a point where I can do anything it's impossible to get in to disable things.

I really don't want to have to reinstall Ubuntu just because of this, but looking around on the net there seems to be little evidence of this happening before.

Anyone know where I should start?

Thanks, Giles.

---

### Post by P4man on 2009-09-14
silly question perhaps but are you sure the machine turns off, and its not just the display (or backlight) turning off ?

Something else you could try to help pinpoint the problem, is booting in to recovery mode and create a new user, and log in using that user.

If needed, press escape during boot to show the grub menu, select "recovery mode" and then a root shell.

there create a new user:

```
adduser testuser
passwd testuser
```
(enter a pw).

then reboot
```
reboot
```
and try logging in with the new user

---

### Post by gilester on 2009-09-18
Hi, thanks for the suggestion. It was definitely a full power off, the power light went off as well.

I booted into the recovery mode, didn't actually make any changes then rebooted. And as if by magic, the machine is now working fine.

I have no idea what was wrong or how it came to be fixed..

Cheers, Giles.

---

