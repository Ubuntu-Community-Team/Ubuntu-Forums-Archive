---
title: "&quot;one or more disks are failing&quot; warning from disk utility in karmic"
date: 2009-10-31
forum: General Help
---

### Post by bhuvi on 2009-10-31
i recently installed ubuntu karmic in a laptop and i get a warning from the disk utility and it says the disk has too many bad sectors and it also says to "back up all data and replace the disc".it is a fairly new laptop and is only a year old.what should i do,would the hard disk fail such quickly?

---

### Post by dependancyhell on 2009-10-31
sudo apt-get install smartmontools

Then

sudo smartctl -a /dev/[disk]

Where [disk] is the disk you're having problems with.

This will give you full SMART statistics.

If it's really a failing disk drive, hopefully, you're still under warranty.

If you're not under warranty, but in the EU, your consumer rights outlast your warranty anyway, so you should still be okay.

---

### Post by bhuvi on 2009-10-31
when i run it and get the smart statistics i get:
SMART overall-health self-assessment test result: PASSED

and in the end it also says:

Error 1 occurred at disk power-on lifetime: 955 hours (39 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 57 a8 bc e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00bca857 = 12363863

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 00 08 50 a8 bc e0 00      00:00:42.167  WRITE DMA EXT
  35 00 08 48 a8 bc e0 00      00:00:42.167  WRITE DMA EXT
  35 00 08 40 a8 bc e0 00      00:00:42.167  WRITE DMA EXT
  35 00 08 38 a8 bc e0 00      00:00:42.166  WRITE DMA EXT
  35 00 08 30 a8 bc e0 00      00:00:42.166  WRITE DMA EXT

is there any thing serious about it??

---

### Post by Bucky Ball on 2009-10-31
Are you dual-booting with Windows? Did you close out of Windows safely (from restart or shutdown) last time you used it? Just an idea.

That IS a very new laptop so warranty will cover hardware defects.

---

### Post by P4man on 2009-10-31
PLease do a search before posting. Here is an informative thread on the same issue:
[http://ubuntuforums.org/showthread.php?t=1305565](http://ubuntuforums.org/showthread.php?t=1305565)

short version: if the error is limited to a high count of relocated sectors, and the number is either negative or insanely high (>1000) then its a bug and not necessarily a reason to worry

---

### Post by bhuvi on 2009-10-31
i have installed ubuntu 9.10 inside vista using wubi.it was shut down correctly the last time.maybe i should run disk check in vista and report back to you later.thanks for the reply

---

### Post by P4man on 2009-10-31
> **bhuvi said:**
> i have installed ubuntu 9.10 inside vista using wubi.it was shut down correctly the last time.maybe i should run disk check in vista and report back to you later.thanks for the reply

chkdsk doesnt test[ smart monitoring]("http://en.wikipedia.org/wiki/S.M.A.R.T.") results. it only checks the filesystem integrity. It will tell you nothing if palimpsest is right or not about warning you for imminent disk failure. If you want a second opinion on the smart test results, use a smart monitoring tool:
[http://en.wikipedia.org/wiki/Comparison_of_S.M.A.R.T._tools](http://en.wikipedia.org/wiki/Comparison_of_S.M.A.R.T._tools)

---

### Post by ibbill on 2009-10-31
you may want to take a look at this thread seems to be a glitch.

[http://ubuntuforums.org/showthread.php?t=1299556]("http://ubuntuforums.org/showthread.php?t=1299556")

Bill

---

### Post by bhuvi on 2009-11-02
It seems to be a bug with disk utility.But the count is very low(66) in my case comparing to others who have much higher values.
Any way running diskcheck utility in vista haven't corrected it.

---

### Post by krishna1650 on 2009-11-02
> **bhuvi said:**
> It seems to be a bug with disk utility.But the count is very low(66) in my case comparing to others who have much higher values.
Any running diskcheck utility in vista haven't corrected it.

i am also facing the problem, here is my statistics.

bad sector: -2 bad sectors

---

