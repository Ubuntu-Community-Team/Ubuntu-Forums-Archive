---
title: "*sigh* Another 9.10 Sound issue"
date: 2010-01-14
forum: General Help
---

### Post by jfowlie on 2010-01-14
I have 32-bit Karmic running. Sound was working correctly after install.

I installed a Plantronics SAVI headset, which worked properly upon selecting it as audio output in Sound Preferences.

After rebooting later in the week, the headset no longer worked. The hardware is detected and available in Sound Preferences, but no sound is heard.

In trying to fix the problem, I have now lost all sound. All the hardware shows up, no errors are reported, but no sound comes out.

Hardware per aplay -l:
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Office [Savi Office], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm not exactly a newbie, but I'm tapped out.

Thanks for any help!
--James

---

### Post by khelben1979 on 2010-01-14
Check in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") to see if you have the possibility to downgrade to your previous Linux kernel to see if it solves the problem.

---

### Post by jfowlie on 2010-01-14
Your idea about Synaptic helped, although in a different way.

I got Synaptic to force a reinstallation of everything related to ALSA and PulseAudio.

Doing so restored my onboard audio immediately.

I will try to downgrade the kernel to see if that gets me back my Plantronics.

I have noted that, in my messages log, the Plantronics was recognized with the following line:
generic-usb 0003:047F:0411.0006: hiddev97,hidraw2: USB HID v1.00 Device [Plantronics Savi Office] on usb-0000:00:1a.0-1.1/input3

However, after the reboot, I get the following message:
generic-usb: probe of 0003:047F:0411.0006 failed with error -22

The Savi continues to show up as an option in Sound Preferences and the PulseAudio Manager, but no output is received.

I'll try the kernel downgrade, as it's obvious that something's changed with regard to the way the kernel is seeing the device.

Thanks!
--James

---

### Post by jfowlie on 2010-01-14
The kernel revert didn't help the Plantronics issue. What used to be properly recognized continues to generate an error -22 upon connection, and sound is not heard.

---

### Post by khelben1979 on 2010-01-14
Hmm.. doing a complete reinstall and then being very careful regarding which updates which are being installed might help.

There is an option of blacklisting kernel modules which might mess up with [udev]("http://en.wikipedia.org/wiki/Udev").
[Howto: Prevent a Linux kernel module from auto loading - nixCraft]("http://www.cyberciti.biz/tips/avoid-linux-kernel-module-driver-autoloading.html")

---

### Post by Blackie_Chan on 2010-01-25
I have the same motherboard and had some sound problems with line-in. Try the following [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359)

After trying the fix above, run `alsamixer` and attach the screenshot.

---

### Post by raymondh on 2010-01-25
I happen to be browsing this blog so maybe, just maybe this read can help

[http://drowninginbugs.blogspot.com/2009_10_01_archive.html](http://drowninginbugs.blogspot.com/2009_10_01_archive.html)

Raymond

---

### Post by jfowlie on 2010-01-26
Well... it's working again.

What I did:
1) Completely purged and reinstalled alsa and pulseaudio;

2) Eliminated the alsa-base.conf and oss-compat.conf from /etc/modprobe.d (I will try and troubleshoot the files later)

3) After a reboot, unplugged power from the Plantronics unit, then plugged it in again. Apparently the Plantronics SAVI Office isn't properly recognized upon USB connection, it needs to be power-cycled and will then be properly detected.

Thanks for all the help... it got me pointed in the right direction!
--J

---

