---
title: "Ubuntu 9.10, lm-sensor install failure?"
date: 2009-12-30
forum: General Help
---

### Post by UnusedUserNameHere on 2009-12-30
Edit 2:

OMG.. I solved the problem. I feel like an idiot. It was because I had a Flash drive plugged into my keyboard's USB port. Apparently Linux can't boot while there's a Flash Drive there.

----

I was following the instructions to install lm-sensors here: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Once I rebooted the computer, it'd hang while booting Ubuntu. Recovery mode shows it stops at Booting Processor 1.

I tried booting the Live CD, which used to work, but now that also hangs.

I added the "acpi=off" line, and can boot fine, however my input devices work REALLY slow now. And I get an error after logging in that CPU Frequency scaling is not supported.

I am only able to type about 1 character per second, if I type any faster, keys are dropped. The mouse moves really slow as well.

Everything was working fine for weeks, until I decided to try to install lm-sensors.

How can I revert these changes? Something seems to be seriously wrong.

----

Ubuntu 9.10 x86_64
Core 2 Duo E6750
Abit IP35
nVidia G-Force 8600 GTS
3GB RAM

----

Edit:

I have used Synaptic to remove lm-sensors, and also manually removed the added lines to /etc/modules. The problem still persists.

I booted into Win Vista now, and everything is working fine for Windows.

I found out if I boot Linux "noapic" instead of "acpi=off" it hangs on "Checking TSC synchronization" Not sure if this is helpful.

I do not understand how I went from being able to use Linux completely fine for weeks, to not being able to boot either kernel or the live CD without using "acpi=off" by just trying to install lm-sensors. And using "acpi=off" seriously cripples my input devices.

---

