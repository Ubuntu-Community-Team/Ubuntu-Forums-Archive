---
title: "Power button does not shut down"
date: 2010-06-25
forum: General Help
---

### Post by GeoMX on 2010-06-25
We are planning the migration fro Karmic to Lucid for our systems, these systems are custom Ubuntu installations, we create them using debootstrap and then running a script that installs desired packages, mainly X server and (optionally) fluxbox.

I've set up a hard drive with our current scripts (the only modifications were the change of lucid instead of karmic for update servers and removing usplash from our scripts), but I've found that pushing the power button would not shut down the system (we have no GDM or similar), the system does not respond to this event as used to do under Karmic.

Do you know where I can check/enable the system to shutdown when pushing the power button?

Thanks in advance for your help.

---

### Post by gzarkadas on 2010-06-25
I am still to Karmic, so I will not be able to be much of a help, but check that all your hardware is supported by Lucid. There have been issues with drivers and yours seems like that kind of issue. Do a `sudo lshw | less' and watch the output for UNCLAIMED devices (specifically components of the motherboard).

---

### Post by supergrav on 2010-06-25
> **GeoMX said:**
> 
Do you know where I can check/enable the system to shutdown when pushing the power button?


Have you tried System>Preferences>Power Management in General tab?

---

### Post by GeoMX on 2010-06-26
I also found that I didn't have support for USB devices, tried with an USB mouse and two USB memory sticks. Solved installing usbutils package. It behaves a bit erratic tough.

> **gzarkadas said:**
> I am still to Karmic, so I will not be able to be much of a help, but check that all your hardware is supported by Lucid. There have been issues with drivers and yours seems like that kind of issue. Do a `sudo lshw | less' and watch the output for UNCLAIMED devices (specifically components of the motherboard).
I have no unclaimed devices.

> **supergrav said:**
> Have you tried System>Preferences>Power Management in General tab?
I don't have a desktop manager installed, only fluxbox (and another system without it, just console), so I can't use that power management assistant.

---

### Post by GeoMX on 2010-06-26
This reading [http://mailman.linuxchix.org/pipermail/techtalk/2006-September/021393.html](http://mailman.linuxchix.org/pipermail/techtalk/2006-September/021393.html) pointed me to the fact that I was missing acpi support, installing it solved my problem with the power button :).

Guess debootstrap differs between Karmic and Lucid in the software it installs, but don't know where to find info about it.

I can continue with my testing, hope I can figure out the cause of usb erratic behavior (sometimes the system does not recognize my USB mouse).

---

### Post by gzarkadas on 2010-06-26
Nice to hear that the problem solved :). You can, if you have a backup of /var/lib/dpkg/status of the old system (or another one if they have the same config) to compare it with the same file of the new system to see if there are other packages that are also missing.

---

### Post by GeoMX on 2010-06-26
I have three hard disks, one with full Karmic (everyday use), another with custom Karmic installation (the one used for our systems) and the last with custom Lucid installation (created with same process than custom Karmic, but I'm testing it before migrating), I select which one to start at boot.

Thanks a lot for the tip, it'll be really useful :).

---

