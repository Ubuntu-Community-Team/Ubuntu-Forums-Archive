---
title: "Writing udev Rules for any USB plugged"
date: 2010-04-19
forum: General Help
---

### Post by venkivoice on 2010-04-19
Hi There,

I have read about udev and come to know it would work only when we are giving setting up the specific names and size of the USB in rules.
Below is my USB Detect fr udev rules

SUBSYSTEM=="block", SUBSYSTEMS=="usb", KERNEL=="sd?", RUN+="/usr/local/bin/usb.sh"

The script not get executed. Please guide me how to udev rule for generic USB plugged.

Thanks & Regards
Venkat

---

