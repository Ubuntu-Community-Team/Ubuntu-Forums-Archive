---
title: "Can't permanently mount a Windows Share folder"
date: 2011-01-07
forum: General Help
---

### Post by Erdr1ck on 2011-01-07
I'm successfully accessed a local Windows Share folder with the "Places --> Connect to Server" tool, but I can't figure out how to get it permanently mounted so that I don't have to keep logging in every time I boot up.

I understand that the solution is supposed to involve adding a line to fstab, but I've tried a dozen variations on it based on various tutorials I've found online to no avail.

Is there any way to check and see how the "Connect to Server" tool is doing its magic?  Or to make that permanent?

-Brett Bowman
Erdr1ck

System:
Ubuntu 10.10 (AMD64)

---

### Post by TeoBigusGeekus on 2011-01-07
Have you looked at bohdi's guide [here]("http://ubuntuforums.org/showthread.php?t=283131")?

---

### Post by dcstar on 2011-01-07
> **Erdr1ck said:**
> I'm successfully accessed a local Windows Share folder with the "Places --> Connect to Server" tool, but I can't figure out how to get it permanently mounted so that I don't have to keep logging in every time I boot up.
.......

Install the **pysdm** package and use that.

---

