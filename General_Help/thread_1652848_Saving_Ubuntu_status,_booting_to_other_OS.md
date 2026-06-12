---
title: "Saving Ubuntu status, booting to other OS?"
date: 2010-12-25
forum: General Help
---

### Post by Psyael on 2010-12-25
I have an Ubuntu desktop that I do not want to permanently close, with material that will disappear forever in a shutdown when the cache is cleared. But I need to use a Windows environment, and have a dual boot drive with Windows and Ubuntu partitions.

Hibernate supposedly saves all data in RAM somewhere and off's the computer to the point where it's using no power (or as little as a shut down). When restarted, a complete start from POST happens and all material is restored as it was. What does hibernate write all my cache to? **Can I hibernate Ubuntu, reboot from POST and choose to boot into Windows, do my business there, then reboot again into Ubuntu and have my desktop restored?**

Failing that, is there another method to essentially run Ubuntu and Windows at the same time? Running my needed Windows app in WINE is out of the question, since I want to use iTunes and an iPod Touch that is not very well supported in Ubuntu.

---

### Post by dcstar on 2010-12-25
> **Psyael said:**
> 
Hibernate supposedly saves all data in RAM somewhere and off's the computer to the point where it's using no power (or as little as a shut down). When restarted, a complete start from POST happens and all material is restored as it was. What does hibernate write all my cache to? **Can I hibernate Ubuntu, reboot from POST and choose to boot into Windows, do my business there, then reboot again into Ubuntu and have my desktop restored?**


**Suspend** saves to RAM, **Hibernate** saves to disk.

---

### Post by Habeouscorpus on 2010-12-25
I remember reading somewhere that this was not possible for a dual-boot. However, I believe the page referred to a Wubi installation. But! The internet yields results: 

> I use both Windows and Debian GNU/Linux on my netbook. I hibernate them both and choose one on awakening and have had no problems whatsoever. I also have a shared data partition similar to what you describe. I use NTFS (which is fully supported by recent Linux releases) and have had no problems.

Ubuntu (and Linux in general) hibernate to a swap partition. That is, the contents of RAM are saved to this extra partition. Windows saves to a swap area in its own partition (by default). The two images are in totally different places and cannot interfere with each other.

From: [http://superuser.com/questions/211079/what-do-i-have-to-take-care-of-when-hibernating-both-ubuntu-and-windows-dual-boo](http://superuser.com/questions/211079/what-do-i-have-to-take-care-of-when-hibernating-both-ubuntu-and-windows-dual-boo)

---

