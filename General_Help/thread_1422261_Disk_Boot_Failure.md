---
title: "Disk Boot Failure"
date: 2010-03-05
forum: General Help
---

### Post by zerena on 2010-03-05
Hi,

My 9.04 was working fine. We usually keep the computer on and don't restart very often. Last night, we turned off the computer, and when we turned it on this morning, it said DISK BOOT FAILURE and something about insert system disk and press enter. I can boot from the disk.

Now here's the thing. About a month ago, it would make a Beeeeep beep beep noise when we turned it on and nothing would happen. So we took it to get it fixed, and the guy moved some fuse thingys and then it seemed to work okay. The only problem was this disk boot failure message, so I took it home and reinstalled ubuntu from the cd and all was fine. 

I don't understand why it's doing this again. It was working fine. Was there something in a recent update that caused it? If so, can I un-update?

Help, please.

---

### Post by ibuclaw on 2010-03-05
> **zerena said:**
> Hi,

My 9.04 was working fine. We usually keep the computer on and don't restart very often. Last night, we turned off the computer, and when we turned it on this morning, it said DISK BOOT FAILURE and something about insert system disk and press enter. I can boot from the disk.

Now here's the thing. About a month ago, it would make a Beeeeep beep beep noise when we turned it on and nothing would happen. So we took it to get it fixed, and the guy moved some fuse thingys and then it seemed to work okay. The only problem was this disk boot failure message, so I took it home and reinstalled ubuntu from the cd and all was fine. 

I don't understand why it's doing this again. It was working fine. Was there something in a recent update that caused it? If so, can I un-update?

Help, please.
"DISK BOOT FAILURE" is not a message I'd associated with Linux. (As this message will most likely occur during the initial SBIOS checks).

Sounds like your Hard Drive is dying if I'm completely honest.

Regards

---

### Post by zerena on 2010-03-05
Ok, so is there any way to confirm that it's a dying hard drive causing it? I Do have another internal hard drive that I could put a linux partition on. I'd hate to have to start again if I don't have to, though.

When I boot from the ubuntu cd, it sees the hard drive and everything. Anything I can do here?

---

### Post by ibuclaw on 2010-03-05
> **zerena said:**
> Ok, so is there any way to confirm that it's a dying hard drive causing it? I Do have another internal hard drive that I could put a linux partition on. I'd hate to have to start again if I don't have to, though.

When I boot from the ubuntu cd, it sees the hard drive and everything. Anything I can do here?

You can try using smartmontools.

Can be installed via command-line:
```
sudo apt-get install smartmontools
```

And you can print information of your device via:
```
sudo smartctl -a /dev/sda
```

There is also a GUI application named palimpsest, that may be in your System->Administration menu under "Disk Monitor".

Regards

---

### Post by zerena on 2010-03-05
I'm so proud of myself! I'm not very computery when it comes to command line stuff, and I decided to go ahead and reinstall. I was thinking of doing a reinstall as a dual boot, just so the computer would start up, then when I had to choose which one to boot, I'd boot the old one. When I went to install, the hard drive that showed up as the default was my second internal hard drive, the one where I store data, that has no OS on it. At that point, I realised that for some reason the BIOS was showing that as the primary drive.

So I went to the BIOS setup thing, went to the hardware and switched the hard drives around so the first was second and the second was first. Voila, it booted up like nothing had happened.

Problem solved, but the question remains, what caused the BIOS to switch hard drives? I've been using this install for about 6 weeks now. We've restarted before with no problems. Is it possible that an update to Ubuntu caused the BIOS to switch hard drives around? I really don't go messing around with the BIOS, nor do I do terminal-type stuff unless absolutely necessary. 

What caused it????

---

