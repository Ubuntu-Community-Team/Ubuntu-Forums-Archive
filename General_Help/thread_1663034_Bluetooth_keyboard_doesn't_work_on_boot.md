---
title: "Bluetooth keyboard doesn't work on boot"
date: 2011-01-09
forum: General Help
---

### Post by Darius_ on 2011-01-09
Hi,
I have an apple BT keyboard and it does work, but have to unplug and replug the USB BT dongle after I login before it works.

I am wondering if there is a program that gets run when the dongle is connected (via hal or something..) which hooks it up somehow, but I have no idea where to look for it.

There aren't any persistent daemons which are running when it works vs when it doesn't that I can see..

---

### Post by darkhelmetchris on 2011-01-09
> **Darius_ said:**
> Hi,
I have an apple BT keyboard and it does work, but have to unplug and replug the USB BT dongle after I login before it works.

Is this behavior happening on an apple?  Do you perhaps have a Dell instead?  What kind of computer is it?

If you have a PC, then I do have one suggestion.  I suspect that your BT dongle is a USB device, and so in your BIOS, try turning off "USB Legacy" or test some other changes to the way your USB devices are detected at boot time.  I have seen many types of USB devices get "stuck" at boot time until they are replugged later.  An addition of a small USB hub may correct the problem also.

---

### Post by Darius_ on 2011-01-09
It's a PC I built myself (Core2Duo ICH9).

I am pretty sure the USB dongle works at a boot for, eg: hcitool scan, but I'll try your suggestion.

---

### Post by Darius_ on 2011-01-09
No change by disabling USB legacy support in the BIOS :(

Also, note that, eg, hcitool scan works after a boot but the keyboard is not "connected".

---

### Post by darkhelmetchris on 2011-01-09
Okay, let's see what else you have connected.  Please post the output of your "hcitool scan" as well as:
```
lsusb
```

---

### Post by Darius_ on 2011-01-09
The only other BT device is a PC, ie

[mythtv 20:43] ~ >hcitool scan
Scanning ...
	58:B0:35:79:0B:2E	Ur

The keyboard isn't visible once it has been associated.

lsusb is..

Bus 008 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0db0:1967 Micro Star International Bluetooth Dongle
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by darkhelmetchris on 2011-01-09
I'm wondering if enumeration of your USB devices during startup is somehow causing your BT dongle to disconnect your keyboard.  I think my first suggestion must be to disconnect all other USB devices (your SoundGraph remote and your Alcor flash drive from what I can see, any others if there are some) and test with just the one USB device, the BT dongle.  I think it's a good test to eliminate any stray data being sent to other USB devices first. Please post your results so we can see if there is any difference at all.  Please add the "hcitool scan" and the "lsusb" from that boot - there could be other clues in that configuration.

As a second test, and I know, I know, this is silly, but.. read this whole thing before you shoot me:  put some fresh batteries (from a different lot) in the keyboard.  I was called in to a customer only last month that has a nice Apple BT keyboard and mouse, and he was complaining that even after changing the batteries to new ones, it kept disconnecting.  The catch, of course, was he put in batteries from the same lot - after testing the batteries, I found them to ALL be bad in that set (a nice pack of 36), even though they were good, name brand new batteries and not dollar-store junk - they were clearly bad.  After he bought a new set, everything was great.  Silly, I know, and I hate saying "did ya check the batteries?" .. and I wouldn't if I had not seen it with my OWN eyes.  But.. there it is.

---

### Post by Darius_ on 2011-01-09
Coincidentally I did recently put new batteries in, no change.

I will look at unplugging the other USB devices but I seriously doubt it's an issue. USB is point to point.

---

### Post by darkhelmetchris on 2011-01-14
I'm wondering how you made out with this after unplugging other USB devices.  Any luck?  I realize that USB is point to point, but I was thinking of the device investigation as Ubuntu starts up.  Your keyboard might be "confused" when it is initially probed by Linux depending on what other hardware is found.  Device probing is not always cut-and-dry in my experience.

As I think more about this, I wonder...  if you happen to have a PCI-USB card laying around, do you experience the same problem using another USB controller?  Does this problem happen if you use it with another computer and a LiveCD?  Both good tests.

Also, I had suggested earlier... have you tried adding a USB hub?  I have used this method for a few stuck devices this way in the past.  For example, I have seen three different models of HP inkjet printers with built-in card readers cause some very odd behavior until replugged after startup.  A small USB hub corrected that instantly.  True, it's only a work-around, but.. pretty easy to try and better than replacing other hardware that may be expensive.

These things might help us narrow things down.

---

