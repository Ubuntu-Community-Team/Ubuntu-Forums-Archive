---
title: "Special keys disable left-click"
date: 2010-10-18
forum: General Help
---

### Post by ravrahn on 2010-10-18
I installed Ubuntu 10.10 on my Windows machine a couple of days ago via wubi (with no partition), and it seems to be working. However, I have a problem:

When I press any of the 'special' keys on the keyboard (Vol up, down, mute, and various others), the left-click on my mouse disables. I'm using a Microsoft Digital Media Keyboard 3000, which has a lot of special keys (and the f keys are special by default), so I've been having trouble not disabling my mouse.

Anyone know what the problem is, how to resolve it? And on top of that, how do I make the special keys work?

---

### Post by forza.stiinta on 2010-10-18
I have the same issue. Can't figure out why - whenever I use the keyboard's special keys, left click dies... however, unplugging the usb dongle (I use a wireless microsoft kit), and pluggin it is again, it left click stats to function... until I use special keys again.

---

### Post by m3topaz on 2010-10-19
I have exactly the same thing - it's been driving me scatty and I only just realised the connection ](*,)

[10.10 x64 Dell Studio 15 Microsoft Digital Media Keyboard 1.0A + Intellimouse Optical. Exactly the same setup worked great with 10.04.]

I tried everything logical to fix - like changing mouse settings, desktop effects, and so on. I couldn't see anything useful in the syslog. This seems to be inherent to Maverick.

For now I need to work so I'll just be careful with the external keyboard. Will try to look harder later on this week.

---

### Post by ravrahn on 2010-10-20
I found a Bluetooth keyboard in my garage and hooked it up, the special keys (just volume up and down on this) work fine, no disabled mouse. It's an original Apple Wireless Keyboard, FWIW.

If that's an option I recommend it, it seems to be an at least temporary solution.

---

### Post by forza.stiinta on 2010-10-27
It's driving me crazy... I use the multimedia keys quite a lot...

---

### Post by Squish on 2010-10-30
This too has been driving me crazy, as I just installed 10.10 [64]. The way to fix this is to unplug and replug the keyboard dongle back in, but I would hardly consider this "Fixing".

Help~

---

### Post by Mr. Wishes on 2010-11-02
I've been getting the same thing. Again, it's a Microsoft multimedia keyboard. The following lines in the xorg log are interesting:
> ...
[ 10230.072] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event6)
[ 10230.072] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[ 10230.072] (**) Microsoft Wired Keyboard 600: always reports core events
[ 10230.072] (**) Microsoft Wired Keyboard 600: Device: "/dev/input/event6"
**[ 10230.092] (II) Microsoft Wired Keyboard 600: Found 1 mouse buttons**
[ 10230.092] (II) Microsoft Wired Keyboard 600: Found scroll wheel(s)
[ 10230.092] (II) Microsoft Wired Keyboard 600: Found relative axes
[ 10230.092] (II) Microsoft Wired Keyboard 600: Found absolute axes
[ 10230.092] (II) Microsoft Wired Keyboard 600: Found x and y absolute axes
[ 10230.092] (II) Microsoft Wired Keyboard 600: Found keys
**[ 10230.092] (II) Microsoft Wired Keyboard 600: Configuring as mouse**
[ 10230.092] (II) Microsoft Wired Keyboard 600: Configuring as keyboard
[ 10230.092] (**) Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[ 10230.092] (**) Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 10230.092] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD)
...


So it could be caused by/fixable with changes to xorg.conf keyboard drivers. I don't have time to fiddle at the moment, I'll just not use the media keys.

---

### Post by Squish on 2011-01-31
This not been fixed yet?(*,)

---

### Post by forza.stiinta on 2011-01-31
For me it got fixed when i updated ubuntu.

---

### Post by lukas_calda on 2011-02-10
I do have the same problem with Microsoft wired keyboard 600. I keep my system updated, but this doesn't help at all. 
Has anyone solved the problem?
Thanks

---

### Post by palo.verde on 2011-02-11
I believe I am having this problem, but I am using an Apple aluminum wired keyboard.  Left click works intermittently.  Mouse works fine when connected to another computer.

IS anyone using 10.10 with the Apple keyboard without issues?

---

