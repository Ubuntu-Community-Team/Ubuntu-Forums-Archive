---
title: "Issue with X in Maverick?"
date: 2011-01-20
forum: General Help
---

### Post by CapnSchmitty on 2011-01-20
Hi, I'm trying to switch from the proprietary FGLRX video drivers to the built-in Xorg drivers under Maverick, and I'm having a bit of an issue.  I followed the steps [here]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") to remove FGLRX and reinstall xorg-ati, and then restarted.

It booted and got to the login screen, but the window and cursor were barely visible, replaced by a bunch of colored horizontal lines.  I logged in "blind" and it switched to my desktop, but the same problem was there.  The taskbar was completely unreadable.  I could remember where my icons were to open the terminal, but it was also distorted beyond usability.  The same was true for all windows.

I restarted into recovery mode and told it to go to failsafe graphics mode, where it started in a low-graphics session, no problem, everything looks great.  But when I start up X, it completely dies and reverts back to its distorted state.

Any suggestions on how to make X work again?  I'm using an ATI Radeon HD4870.  I can just go back to the proprietary drivers if I need to, it's not a huge deal, but desktop effects won't work with those because ATI doesn't like the "Composite Extension" it says it needs to use effects.

---

### Post by CapnSchmitty on 2011-01-20
I also tried running

```
sudo apt-get build-deps xserver-xorg
```

and it installed a bunch of new packages, most of which were libraries or started with "x11", but after rebooting it still looks like a train ran it over and then a tornado hit the remains.

Also, don't know if this is relevant, but when booting normally I get an error message that says "Error during ACPI methods call" before it gets to the login screen.

---

### Post by CapnSchmitty on 2011-01-20
Eh, forget it.  Back to FGLRX.

---

### Post by goldcaddy77 on 2011-02-11
> **CapnSchmitty said:**
> Eh, forget it.  Back to FGLRX.

Yup, I'm doing the same - have 2 ATI Firepro 5700s.  There is only so much googling you can do with the combination of:

ubuntu 
acpi 
dell
radeon 
ati		 - 	
"error during acpi methods call"
atif ubuntu
pnpbios=off
"failure to evaluate atif got ae_bad_parameter"
"checking battery state error during acpi call"

etc... I guess Ubuntu and Dell/ATI really don't play well together.

---

