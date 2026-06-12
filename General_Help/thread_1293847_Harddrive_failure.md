---
title: "Harddrive failure"
date: 2009-10-17
forum: General Help
---

### Post by SilverShadow118 on 2009-10-17
I decided to test karmic. I like it and all, but it says that one of my hard drives is failing which I find odd because its not even two months old.

I booted back into 9.04 and it says it's fine. Are the hard drive tests in karmic inaccurate or is my hard drive dying? Can I more accurately test my HDD's health? Any one else had similar problems?

Thank you

---

### Post by Gizenshya on 2009-10-17
I don't know wat each uses to measure the health of hard drives, much less which one is more accurate.  However, practically all newish drives (within the last 5 years or so) have a system called S.M.A.R.T.  That system monitors various drive parameters and compares them to known ranges from programmed statistics.  Whenever any one of the parameters is outside a given range from the statistics, the smart status is "BAD."  If it ever reads BAD, backup your files immediately and replace the drive.

This will eventually happen to all of them, because hard drives have physical moving parts that cannot last forever.  They usually last years, but certainly have the potential to go bad in weeks or months.  smart status can be either OK or BAD.  Some programs can read the log files from the drives and give you specifics, though.  I only knows of windows programs that do this.  They probably exist for linux, but I just don't know about them.  RivaTuner is a win program that reads the SMART status of hard drives.  It is also a very useful program.

Whenever your computer starts up it checks the SMART status of each drive (if the drive supports it).  And it reports it on screen just after the POST tests.  Just look at your monitor when your computer boots and it will display there.  Some manufacturers of packaged computers (Dell, HP, Compaq, etc.) have splash screens at boot that hide these readouts.  Just look at their splash screen and it will show you a button to press to get into the BIOS (sometimes called "setup").  Then disable the splash screen to see the readouts.

It is also worth noting that 1.  Once a hard drive reaches BAD status in any category it can never be labeled as OK again.  It is permanently BAD.  This status is stored locally on the drive, so it reads the same regardless of what computer it is connected to.  and 2.  If a hard drive's SMART status is BAD, all BIOS's that check SMART status (effectively all mobos within the last 5 years at least) stop the boot process every time the computers boot and tell you that the status is bad and to backup and replace the drive immediately because failure is imminent.  It then requires you to type some awkward key to proceed (to make sure you read the message at least once).  So if the status is bad, you WILL know it.  they don't just go bad and try to hide it.

So, I strongly suspect that your hard drive is perfectly fine.  Follow one of the methods above to make sure the SMART status is OK, but since you aren't getting that boot message, you are probably fine.

---

### Post by cariboo on 2009-10-17
Even new hard drivers fail. Go the the manufacturers web site and download their diagnostic tools. Run them, that way you will know for sure. When the applet first came out it notified me that one of my drives was failing, running the diagnostic tools showed that the drive was OK, even though there were 11 bad sectors, I now use the utility to keep an eye on the hard drive, once the bad sectors start getting close to the threshold, in this case 35, I can still back the data up before it dies completely.

---

### Post by SilverShadow118 on 2009-10-17
Thank you!

---

### Post by oldfred on 2009-10-17
You can download from synaptic a smart control list tool:
smartmontools

---

### Post by Duckter on 2009-10-18
I have the exact same problem.  My drive has been seemingly fine until I thought I'd try out 9.10 and now BAM! 'One or more disks are failing'

Back to 8.10 and nothing, 9.04... nothing, 9.10... 'One or more disks are failing'

No reports of any problems from the BIOS and using the utility suggested I get...

```
sudo smartctl -H  /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

Any more thoughts?

---

