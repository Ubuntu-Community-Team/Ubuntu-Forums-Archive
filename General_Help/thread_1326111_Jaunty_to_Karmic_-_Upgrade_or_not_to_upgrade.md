---
title: "Jaunty to Karmic - Upgrade or not to upgrade?"
date: 2009-11-14
forum: General Help
---

### Post by Lockheed on 2009-11-14
I installed my 64bit 9.04 about seven months ago and since then I made loads of modifications to it, ranging from power saving tweaks to replacing nautilus with pcmanfm (also as desktop manager). I upgraded kernel, configured exotic hardware, replaced a lot of the default software, after long struggle managed to make hibernation and microphone work, even made office 2003 work in 80% of cases. Overall, only after I made many, many, many things to it, I was somewhat comfortable with it being my main operating system.

Now, I would like to upgrade to Karmic Koala (mostly because I hope my wifi switch and custom boot-up splash screens would finally work) but before I do that, I need to know precisely what&#8217;s gonna happen to all the hard work I put in customizing ubuntu up to my requirements.

Can some experienced users speak their mind on this matter?

---

### Post by howefield on 2009-11-14
I think you know the answer to your question.

Image your disk, protect yourself in the event that something goes wrong. Worst case scenario should be having to re image back to your starting point.

It isn't hard.

---

### Post by jnorthr on 2009-11-14
first reports on 9.10 networking are not favorable, you might delay a few more weeks til they are sorted. You should always copy off your valuable data BEFORE you doing any upgrades/reinstalls. Suspect you will loose all your hard tweeking work on a fresh install as the /home partition will probably be blitzed and this is where many tweek settings are held.

---

### Post by MartyBuntu on 2009-11-14
> **howefield said:**
> 

Image your disk, protect yourself in the event that something goes wrong.


This is exactly what I do before any major upgrade, as well as regular backing up. Makes sense.

---

### Post by Lockheed on 2009-11-14
> **howefield said:**
> Image your disk, protect yourself in the event that something goes wrong.

The problem is I am using ext4 on all partitions and I do not know which imagining software supports it fully.

---

### Post by howefield on 2009-11-14
> **Lockheed said:**
> The problem is I am using ext4 on all partitions and I do not know which imagining software supports it fully.

Errmm, I am using Clonezilla with my ext4 install and do not have issues with either creating nor restoring images.

*"        * Filesystem supported: ext2, ext3, ext4, reiserfs, xfs, jfs of GNU/Linux, FAT, NTFS of MS Windows, and HFS+ of Mac OS. Therefore you can clone GNU/Linux, MS windows and Intel-based Mac OS, no matter it's 32-bit (x86) or 64-bit (x86-64) OS. For these file systems, only used blocks in partition are saved and restored. For unsupported file system, sector-to-sector copy is done by dd in Clonezilla." *

The commercial Acronis, which I like, can only support ext4 with sector by sector backups, so you end up with enormous backups.

---

### Post by Lockheed on 2009-11-14
Image is done. Let's see how upgrade goes.

---

