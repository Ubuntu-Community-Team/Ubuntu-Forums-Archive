---
title: "Reallocated Sector Count WARNING"
date: 2011-09-25
forum: General Help
---

### Post by ki4jgt on 2011-09-25
I've had the same sector count for the last year. It has never been in red and displayed WARNING before though. Here are the stats as they have been for the last year.

Normalized: 100
Worst: 100
Threshold: 36
Value: 18 Sectors

Like I said, it hasn't change any in the last year, but now, it's got a BIG RED WARNING label.

---

### Post by tgalati4 on 2011-09-26
It's normal for the platter to degrade over time, so relocating sectors is something that happens automatically.  When the sector count grows beyond the drive controller's ability to manage them, you have a problem.  The SMART parameters aren't helpful unless you know how to read them for your particular drive.  For instance, the normalized value is 100 or possibly 100% good.

So as your bad sector count grows, your SMART normalized value will go down until a warning is issued.  In this case it looks like 36%.  It's possible that the sector count on your drive grew very quickly (due to some other mechanical problem) that created the warning before actually updating the SMART parameters on the drive's EEPROM.

Since the relocated count did not change, perhaps some other SMART parameter is triggering the warning.

Back up your data right away, regardless of whether the warning is real or not.

---

### Post by dcstar on 2011-09-26
> **ki4jgt said:**
> I've had the same sector count for the last year. It has never been in red and displayed WARNING before though. Here are the stats as they have been for the last year.

Normalized: 100
Worst: 100
Threshold: 36
Value: 18 Sectors

Like I said, it hasn't change any in the last year, but now, it's got a BIG RED WARNING label.

The decision as to what is acceptable and what is not can change with updated software packages, it is possible an updated package is now more sensitive to this particular SMART attribute (or it could be a bug in the reporting package).

Either way, you don't really want to be using a drive with too many Reallocated Sectors, it usually indicates impending trouble.

---

