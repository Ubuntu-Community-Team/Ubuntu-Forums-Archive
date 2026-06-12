---
title: "Stuck on Verifying DMI Pool Data"
date: 2010-12-01
forum: General Help
---

### Post by KillerSiafu on 2010-12-01
My Media PC that I built a few years ago was running fine up until last week. It's running 10.04. Last week I noticed there were some updates to install (besides the upgrade to 10.10 which I planned on doing soon). I installed the updates and afterwards it asked me to restart the computer. After it rebooted, it hung on Verifying DMI Pool Data and wouldn't boot past that stage.

The computer has one hard drive that contains the operating system and four hard drives in a software RAID 5. Over the past few weeks, the computer's been complaining about one of the drives in the array being in danger of imminent failure; which was obviously one of the possible causes of the issue that came to mind. I've tried spinriting the drive but it seems to be beyond repair. I've since purchased a new drive but haven't replaced that one yet...

First, I went into the bios and checked the standard things:
[LIST]
[*]Boot Order Is Correct
[*]Hard Drive Boot Priority is correct
[*]All the hard drives are being detected
[*]etc
[/LIST]

After checking that I tried rebooting, no luck. Then I went in and restored the bios factory defaults, again double checked the above items, and rebooted; no luck.

I then unplugged all unnecessary cables and rechecked that all the ones that were still plugged in were secure; no luck.

I also tried booting to the Live CD just to see if it would work, which it did, but after I rebooted and tried to boot from the hard drive again I was right back to where I was. I brought up the drive manager while I was on the Live CD and it was still complaining about the one drive.

Then I tried spinriting the hard drive the contains the operating system; no luck.

Next I opened up the machine and tried removing the mobo battery and resetting CMOS; no luck.

Then I unplugged all of the hard drives in the raid array and rebooted again with just the operating system drive attached. I made sure the cables were secure and checked the bios and it showed that as the only drive and it was the first drive in the boot order, etc; no luck.

I then pulled out the operating system drive and plugged into a hard drive dock that I have, which I then plugged into my laptop. I just wanted to confirm that the drive was readable, which it was.

I plugged the drive back in and turned the computer on; still no luck.

At this point I'm running out of ideas... Anyone?

---

### Post by KillerSiafu on 2010-12-03
I was able to solve the issue... finally.

I repaired the MBR on the operating system drive. I followed the guide here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

