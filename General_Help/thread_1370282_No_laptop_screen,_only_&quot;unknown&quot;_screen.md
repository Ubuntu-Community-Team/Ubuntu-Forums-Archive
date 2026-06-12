---
title: "No laptop screen, only &quot;unknown&quot; screen"
date: 2010-01-02
forum: General Help
---

### Post by Udibuntu on 2010-01-02
Hi,

I have tried to connect my GMA500 based Acer 751 to an external dsiplay via VGA connection.

I couldn't get the right resolution on the external screen (1920/1080) so I disconnected it and rebooted.

Now there is only an "unknown" screen in the display menu.

I have rewritten the xorg conf file per instructions for enabling GMA500 but to no avail - conf file looks right but screen is "unknown", low resolution and 4:3 aspect ratio, instead of 16:9.

Please help me restore to laptop monitor - I think I can take from there to enable the right resolution.

Thanks,

Udi

---

### Post by uffek on 2010-01-02
Do you have any "known" external monitors to try? Possibly with correct resolution?Are you on 9.10 ubuntu or somethig older? A command   sudo dpkg-reconfigure -phigh xserver-xorg    restored defaults on 6.06 but I haven't tried it on newer ones.

---

### Post by Udibuntu on 2010-01-02
> **uffek said:**
> Do you have any "known" external monitors to try? Possibly with correct resolution?Are you on 9.10 ubuntu or somethig older? A command   sudo dpkg-reconfigure -phigh xserver-xorg    restored defaults on 6.06 but I haven't tried it on newer ones.

Thank you, I'm on Karmic.

I'm reluctant to try this command, due to the fact that this is a much diffrerent realease.

---

### Post by Udibuntu on 2010-01-03
Bump. Help..

---

### Post by Udibuntu on 2010-01-11
Solved by removing and reinstalling the psb driver. xrandr does not work well with current psb driver.

---

