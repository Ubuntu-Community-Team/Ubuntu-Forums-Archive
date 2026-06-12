---
title: "USB problems"
date: 2009-09-10
forum: General Help
---

### Post by corevalue on 2009-09-10
Running 9.04 on AMD platform. Running 8.04 on the same hardware had NONE of these issues.

(1) Couldn't install from a live CD on USB CDROM. Until that is, I found out that unplugging the USB CDROM, and re-inserting it during the boot process, got it to work. I I had to do a re-install, because the upgrade to 8.10 left me with no network connection.

(2) Pinnacle 72e USB TV successfully installed, correct status in dmesg (...found in warm state...). Does not work if the USB stick is plugged in during boot. Works fine if the stick is plugged in AFTER boot.

(3) USB memory stick not automounted, if plugged in during boot. Discovered and works fine if plugged in AFTER boot....

(4) Logitech USB speakerdiscovered and work OK if run from the system settings dialog ("test sound"). But no sound from a player application, even though I can see the visualisations as it plays.

---

### Post by P4man on 2009-09-11
> Until that is, I found out that unplugging the USB CDROM, and re-inserting it during the boot process,

What do you mean by boot process? Is that the BIOS POST you're talking about, before grub even, or when the linux kernel is booting? If its the former, then your problem is BIOS/hardware related, perhaps too much powerdraw on your USB hub?

If its the latter then... Id consider filing a bug report on launchpad.

---

### Post by corevalue on 2009-09-11
I had to unplug the USB CD drive post BIOS, during the OS boot when the Kubuntu splash was showing, to get a successful boot from CD and install 9.04. It's not a power draw problem, the same hardware works fine in Windows2000 and Kubuntu 8.04. I found this fix on a forum, so other people have seen this.

The only USB device that works properly is a Trust wireless keyboard, all the other USB devices get reported in dmesg if the computer is booted with them in, but they don't work -  Dolphin can't find any memory stick, Kaffeine finds the correct DVB TV USB stick, but can't tune it properly, the USB speakers, will work from the system settings test panel, but not with a player. Sound comes from the headphone ports so I know it's not an ALSA/PulseAudio problem. I haven't tried the USB CDROM after boot ( I borrowed it for a day).

I see the same messages in dmesg if I plug the devices in after boot - no problems reported with the devices.

It's as if something is scrambling the USB enumeration. Kaffeine, for example, appears to be trying to tune the TV, but the frequencies jump in 33% increments (not normal) and no channels are found, as if it's addressing the wrong device, but works fine if the stick is plugged in late.

Sorry if I wasn't clear in the original post.

---

