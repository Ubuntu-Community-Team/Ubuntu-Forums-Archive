---
title: "Volume is 0 on Boot"
date: 2010-02-14
forum: General Help
---

### Post by Zomaian on 2010-02-14
When I booted Ubuntu for the first time and a few times after that I heard the regular login and welcome sounds but now after updating and installing some software and some other edits the volume sound goes to 0 when I boot my iMac. When I login into an account the volume is set to 0 but works when I level it up. When I change it to 100 for example and reboot the computer the sound changes back to 0.

All the sound and recording works fine so how can I fix this?

Thanks,
Bob

---

### Post by VCoolio on 2010-02-14
Sound muted at startup and using alsa? Feature disabled 'for speed  reasons'. Do this:
sudo mv /etc/rc0.d/K50alsa-utils /etc/rc0.d/S50alsa-utils
sudo mv /etc/rc6.d/K50alsa-utils /etc/rc6.d/S50alsa-utils

reboot
[credits]("http://iainbuclaw.wordpress.com/2009/09/15/howto-save-and-restore-alsa-settings-on-startupshutdown")

If you use pulse audio:
Comment out:
mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
On line 378 or 379 in /etc/init.d/alsa-utils .

[credits]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732/comments/67")

---

### Post by Zomaian on 2010-02-15
> **VCoolio said:**
> Sound muted at startup and using alsa? Feature disabled 'for speed  reasons'. Do this:
sudo mv /etc/rc0.d/K50alsa-utils /etc/rc0.d/S50alsa-utils
sudo mv /etc/rc6.d/K50alsa-utils /etc/rc6.d/S50alsa-utils

reboot
[credits]("http://iainbuclaw.wordpress.com/2009/09/15/howto-save-and-restore-alsa-settings-on-startupshutdown")

Worked like a charm :). Thanks mate!

---

### Post by Jose Catre-Vandis on 2010-02-17
Thanks for this useful tip

---

