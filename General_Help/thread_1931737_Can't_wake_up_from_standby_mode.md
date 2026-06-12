---
title: "Can't wake up from standby mode"
date: 2012-02-26
forum: General Help
---

### Post by calande on 2012-02-26
Hello,

With Oneiric, I'm unable to wake up from standby mode on my desktop computer. When I ask Ubuntu to go into standby mode, it takes 1-2 seconds to do so. When I power on the computer again, I can see the leds of my screen, my SSD, and keyboard (numlock) lighting again, but that's about it. No image, even after hitting the space bar ; numlock is frozen ; the SSD led is continuous even after 15 minutes. The only solution is a hard restart holding down the power button. Here's my bios configuration:

```
Suspend mode          S1 (POS) & S3 (STR)
Repost video on S3 resume          No
ACPI 2.0 support          Yes
ACPI APIC          Enabled
Power Management/APM          Enabled
Power button mode          suspend
Suspend power saving type          C3
Restore on AC power loss          Last state
Suspend time out          Disabled
Video power down mode          Suspend
Power on PS/2 keyboard          Enabled
```

Any idea? Thank you ;)

---

### Post by calande on 2012-03-04
Any idea?

---

### Post by kmir on 2012-03-06
I have the same problem. I don't know the inner workings, but I am assuming it's not telling the monitor to wake up from suspend as well?

---

### Post by Hikayu on 2012-03-06
When you say the numlock is frozen, I'm quite sure that means that the entire system has halted. That statement, by the way, I cannot guarantee.
Have you tried shifting virtual terminals? I do remember, sometimes, when I log out to switch users, it fails to revert to the correct graphic terminal. I resolve it by pressing Ctrl+alt+(F7, F8 or F9)

---

### Post by calande on 2012-03-15
Yes, numlock key is frozen, and hitting Ctrl-Alt-F_ doesn't change anything. My screen turns on but it's black...Any idea? Thanks.

---

### Post by Grant T B on 2012-05-09
I've just had essentially the same problem: I told Karmic, on my eee 901 netbook, to Standby, and it did so, but then became nonresponsive. The screen is black except for a white cursor in the top left. The light indicating that power is on is steady, not flashing as is normally the case when the computer is on Standby. Ctl+Alt+Del produces no effect, nor does pressing the power button. I haven't held the power button to force a shutdown because I gather that this can damage a computer. Can anyone help?

---

