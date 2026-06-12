---
title: "Help! Computer won't boot from hdd!"
date: 2009-07-16
forum: General Help
---

### Post by ron3090 on 2009-07-16
Alright, I've got a major problem. Earlier this morning, my computer worked fine. I had been happily using it and all was well. Then, I turned it off and put all the drives back in the proper order. I had been softmodding my xbox, so it was a mess. I checked all the jumpers, all the IDE cables, everything. It was all fine. I scooted the computer back in place, with a bit of rumbling from the floor's friction, and attempted to boot into Xubuntu. After detecting only two of my three hard drives, it went tp a blinking line on a black screen.
So I went into my BIOS. For some reason, whatever was plugged into the primary IDE master port was listed twice in the boot menu. I thought nothing of it, and tried to boot into Windows on a separate hdd. Same blinking line. I tried to boot from the Xubuntu CD, and that worked, but when I tried to install GRUB from the repair section, it gave several error messages. I was frantic by now.
I unplugged all of my drives, and inserted my CD drive as Primary slave and a blank 40gb drive as primary master. I successfully installed Puppy onto the hdd, but once again, when I tried to boot into it without the CD, the blinking line.

What could this be? Something seems to be wring with my BIOS, but I've never seen anything like this. There are no unusual noises or anything to indicate broken drives. Is my IDE controller fried? I did a lot of hotswapping when modding my xbox, but as I said, it was fine this morning. A note I just remembered: While scooting the computer back, I felt the IDE cords on the motherboard were a bit out of their sockets, so I pushed them back in.

HELP!!!:confused:

---

### Post by rocket16 on 2009-07-16
I am not sure, but have you checked your BIOS? See there, the Boot option from Hard Drive might have got Disabled. If so, enable it, and you may get your reselt. If still the problem exists, you may need to format the Hard Drives and reinstall everything (before which, use Puppy Linux to get your valuable data stored safely). But before that, can you please tell me, whether the XUbuntu Live works or not?If it does, then it may be the problem of your Hard Drive, else the Cords are not set properly, perhaps.

---

### Post by ron3090 on 2009-07-16
This may be the oddest method of solving a problem I have yet seen. A minor option, quiet boot, I think, had somehow gotten disabled. I still don't know what that does, but when I returned my BIOS to the defaults, it was all fine.

Sorry for the trouble. I feel silly.:D

---

