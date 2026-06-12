---
title: "Disable PXE at boot"
date: 2012-10-10
forum: General Help
---

### Post by hawaiiman on 2012-10-10
Running 12.04 64bit . Would like to disable PXE at boot, as it's not useful and takes forever. How?

---

### Post by Lars Noodén on 2012-10-10
From what I recall, that is set in your BIOS.  So reboot and enter the BIOS setup.  The exact location varies a lot depending on the BIOS.

---

### Post by dcstar on 2012-10-10
> **Lars Noodén said:**
> From what I recall, that is set in your BIOS.  So reboot and enter the BIOS setup.  The exact location varies a lot depending on the BIOS.

Yep, nothing at all to do with Ubuntu - all in the hardware.

---

### Post by 6wires on 2012-10-10
...you may use the BIOS to disable it.

---

### Post by hawaiiman on 2012-10-10
Thanks all, yes that was my thought too. However, at startup I see press "delete" to enter setup, but Ubuntu just ignores that and goes ahead and loads. No access to bios. I tried some of the keys for other types of bios, but no joy. Interestingly on a privious install pxe didn't run.

---

### Post by dcstar on 2012-10-10
> **hawaiiman said:**
> Thanks all, yes that was my thought too. However, at startup I see press "delete" to enter setup, but Ubuntu just ignores that and goes ahead and loads. No access to bios. I tried some of the keys for other types of bios, but no joy. Interestingly on a privious install pxe didn't run.

"Ubuntu" has nothing to do with ignoring the BIOS key. The Ubuntu loader starts up AFTER your system has passed that time when you can press that key.

Plug a PS2 keyboard into your system and set the BIOS to use a USB keyboard, this has **nothing** to do with Ubuntu.

---

### Post by hawaiiman on 2012-10-10
My issue was not about a keyboard, usb, ps2, or otherwise. Please do me the courtesy of READING my posts before responding. FYI I suspect this issue is related to GRUB, which starts before Ubuntu. Incidently, I have another machine running Ubuntu and it does not have this issue. It's pretty easy just to hold down the delete key from power on, so give me credit for knowing that much, ok?

---

### Post by Lars Noodén on 2012-10-10
If your boot process has gotten to grub then you are passed  the point where you can enter the BIOS and change settings.  There is a short window of opportunity between the time the machine first turns on (or reboots) and you leave the BIOS.  F2, F10, and Del are commonly used keys to stop the BIOS and enter the setup mode.  But, again, if you've gotten to grub, then you've passed the point where you can enter setup.  The BIOS should flash some information on setup mode very briefly at the beginning.  That's the info you need.

---

### Post by hawaiiman on 2012-10-10
Thank you. Yes, it says press "delete" to enter setup (see above). As I said previously, I hve held the delete key down from power on with the same result. I was just guessing it was GRUB. Bad guess. I'm not trying to pin the issue on Ubuntu either. I just am having a problem, am a Ubuntu fan and user, and looked here for some help. I've been a computer user for over 20 years and have never had this issue. Actually this issue is just an obstruction to getting PXE dissabled at boot, which was the puirpose of the original posting.

---

### Post by Lars Noodén on 2012-10-10
> **hawaiiman said:**
> Thank you. Yes, it says press "delete" to enter setup (see above). As I said previously, I hve held the delete key down from power on with the same result...

Then that's all that can be done.  I'm not a hardware person at all, but did use PXE boot a lot a few years ago.  Could it be possible that it matters whether you press DEL after the Setup message comes up?

---

### Post by hawaiiman on 2012-10-10
Lars, aparently not, unless there's a secret millisecond window I'm missing. I've tried as many combinations as I could think of, and just can't get there. Admitedly not being an expert here, my logic is as follows: bios is working as it boots and I see post report, there is no setting in bios to deny bios access that I'm aware of, I've never had this problem with a windows machine, therefore Ubuntu is on the suspect list. The only others on the list are an exotic hardware failure (it woked this morning before I brought it home), and some sort of attack. Lacking any resolution, I'l take the covers off and check for loose bits which could short the mb. I suppose the only other thing is a format and re-install. Incidently the ps2 mouse port died at the same time. I've also not been able to get the sound utility to recognize the simple speakers I use, although they worked fine with both a prior 32 bit server install, and a prior 64bit server install. It would be convenient to point the finger at the mb, if it weren't for the latter.

---

### Post by hawaiiman on 2012-10-11
Apparently there is an issue with the delete key on this ps2 keyboard. I discovered when I used my wireless keyboard and mouse from my other machine. Got into the bios, but no way to remove "network boot" from the list. Tried settings for PXE , but choices made boot worse. PXE runs before grub. I even did a hard format from an xp disc and re-installed ubuntu, but PXE is still there. Guess it's hopless. Thanks so much for trying.

---

### Post by Lars Noodén on 2012-10-11
At the least, it can be moved down to last in the boot sequence.  But there should be some way to turn it off.  It may not be in the same menu though.

---

### Post by hawaiiman on 2012-10-20
After more research, some of the amibios are hard wired not to allow removing or disabling the boot from network option. Irritating as it better than half the time to boot my server looking for something that's not there. Oh well.

---

