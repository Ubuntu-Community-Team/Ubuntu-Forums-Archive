---
title: "Can't find a valid ISO"
date: 2009-11-09
forum: General Help
---

### Post by d_s_klein on 2009-11-09
I can't find a valid ubuntu-9.10-desktop-amd64 ISO to download.

If I download from bittorrent, it says that 3 files are corrupted.  If I download from the US mirror (I've tried twice) the ISO files are identical.

If I download from a Canadian mirror, one (1) byte is different, but the disk check reports that one file is bad.

I've tried multiple downloads, multiple disk-burns, and I -always- bit compare the disk to the ISO after burning.

---

### Post by Kadajski on 2009-11-09
Have you tried checking if the downloaded ISO md5 hash is correct?

---

### Post by kio_http on 2009-11-09
go to cdimage.ubuntu.com and get your iso

---

### Post by coffeecat on 2009-11-09
> **Kadajski said:**
> Have you tried checking if the downloaded ISO md5 hash is correct?

Agreed. The most important first step.

**d_s_klein**, it sounds as though you are checking each ISO against another and against the burnt discs, but not checking the md5sum of the download. Have a look here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

But if the US mirror ISOs are identical (how did you determine this?) they would probably be uncorrupted. But check the md5sum.

---

### Post by TwiStEr55 on 2009-11-09
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso



check the md5sum of your iso against this value .. if its different, then it is corrupt ... if its the same, your image is genuine :)

---

### Post by d_s_klein on 2009-11-11
Thank you, this helped.  It looks like some mirrors may have corrupted images - it took a couple of tries to get a valid ISO, and there were occasions where the ISOs downloaded from two places were identical and wrong.

Now to get it to install...

---

