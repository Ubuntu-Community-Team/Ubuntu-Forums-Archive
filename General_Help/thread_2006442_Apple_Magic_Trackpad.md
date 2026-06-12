---
title: "Apple Magic Trackpad"
date: 2012-06-19
forum: General Help
---

### Post by Welly Wu on 2012-06-19
I am interested in the Apple Magic Trackpad. I have an ASUS N61JV-X2 notebook PC and I have an ASUS USB-BT211 Bluetooth 2.1 + EDR USB 2.0 dongle. I am running Ubuntu 12.04 64 bit Long Term Support. I already installed sudo apt-get install utouch.

The Apple Magic Trackpad is compatible with Ubuntu. It supports up to 10 gestures at a time. There is a known bug whereby if 11 gestures are entered, X.org server will lock up with Precise Pangolin.

It is kind of expensive at $69.00 USD. However, it is the gold standard for touchpads since it features up to 10 gestures and it has edge-to-edge tracking surface.

Does anyone here have an Apple Magic Trackpad? How well does it work with Ubuntu 12.04 64 bit Long Term Support especially with the utouch package installed?

I am not seriously considering it until I get some replies. It is kind of expensive for my budget, but I can afford it.

As an alternative, I am seriously considering the Logitech Wireless Trackpad for $36.22 USD on Amazon. According to my research, it supports up to two or three finger gestures in Ubuntu 12.04 64 bit Long Term Support. It does require its own Logitech Unifying Receiver instead of Bluetooth which means that I have to dedicate a USB 2.0 or Super Speed USB 3.0 port to use it. I would prefer to use my existing ASUS USB-BT211 Bluetooth 2.1 + EDR USB 2.0 dongle with a trackpad.

This is the sole reason why I am considering the more expensive Apple Magic Trackpad.

---

### Post by rcrath on 2012-06-30
I had a magic trackpad working mostly fully under 11.10, but that functionality is lost in 12.04 when I upgraded.  In order to get the trackpad to work at all, I had to change /usr/shar/X11/xorg.conf.d/60-magictrackpad.conf from evdev to synaptics because it did not work at all in evdev mode, which is workable but less so than before the "upgrade" TO 12.04.  Now I have the equivalent of a no-button synaptics laptop trackpad. :guitar: No 2-finger scroll or any other multitouch except 2-finger right click is working.  I have a bug report filed [here]("https://bugs.launchpad.net/ginn/+bug/1018275"), but no response yet.  The release notes did say magic trackpad support was "coming" in 12.04, but not when.  The logitech looks less attractive to me because of the lack of config options on amazon reviewer pointed out.

---

### Post by Statia on 2013-01-13
I have one, but all it does is registering mouse clicks when I press down on the device. (There are hardware buttons on the underside of the device)
No cursor movement.

(It also works with Android, but of course not with the latest Jelly Bean on my Galaxy Nexus. Just my luck.)

---

### Post by slick_rick on 2013-01-18
Just installed 12.04 and got my Magic trackpad working just now.  The bluetooth pairing went fine, pin is 0000.  After that I could mostly configure it from the mouse/trackpad in the System Settings, but I like triple-tap to be a center mouse click, and there was not  an option for that.  Running synclient TapButton3=2 at the command line fixed that however.

Not sure about the utouch package, I didn't try it as the default drivers seemed to work fine.

GL!

---

