---
title: "Upgrading from 8.04 to 9.10?"
date: 2009-10-13
forum: General Help
---

### Post by wqawasmi on 2009-10-13
How long would it take to download the Update for Ubuntu 9.10 if you have 8.04 on a 512kbs modem? Slow I know but it is all I have to work with at the moment. 

BONUS POINTS: How long would it take if it was 9.04 to 9.10?

---

### Post by ibuclaw on 2009-10-13
AFAIK, you can only go 8.04 -> 8.10 -> 9.04 -> 9.10
And not skip releases.

I may be wrong though, but the last time I upgraded my system several times in one day, I went from 7.04 -> 7.10 -> 8.04 because that is all what update-manager would allow.

Not that it matters, but:
8 months later, I went from 8.04 -> 8.10, 2 months later, 8.10 -> 9.04.
4 months on and I am happy on 9.10 beta :)

Regards
Iain

---

### Post by wilee-nilee on 2009-10-13
You might also look through the Koala part of the forums for more information the mod is correct in their answer. 9.10 is ext4 and grub2 so in your circumstance backup what you want to save and consider a fresh install of 9.10, unless you want to spend a lot of time upgrading only to find your partition extension is the stock 3 up to Jaunty, and possibly borked. I think for us general users that a fresh install with 9.10 is a good idea, unless your a glutton for punishment.

---

### Post by aromo on 2009-10-13
I have a question.  If I wanted to upgrade 3 or more Jaunty installations in my network, is there any way to download the upgrades from Canonical once and point the other computers to take the upgrades from it?  (something kind of like SUS)

---

### Post by ibuclaw on 2009-10-14
> **aromo said:**
> I have a question.  If I wanted to upgrade 3 or more Jaunty installations in my network, is there any way to download the upgrades from Canonical once and point the other computers to take the upgrades from it?  (something kind of like SUS)

Landscape was designed to deploy software across multiple workstations like that.
Have never used it though.

---

### Post by slakkie on 2009-10-14
Their is this changelog in the update-manager package:

```

update-manager (1:0.126) karmic; urgency=low

  * DistUpgrade/DistUpgrade.cfg.hardy:
    - add ability to upgrade from hardy to karmic (as asked for
      by Jonathan Riddell)

```

I haven't checked if that version is in Hardy already, if it is, you can upgrade directly to 9.10. Which would make the update a lot quicker.

---

### Post by Bucky Ball on 2009-10-14
I have a question: Why? Are you looking for stability? Karmic (9.10) is not released yet and is testing. Are you sure you want to test?

If you are looking for stability or are running a production machine which need to be reliable Karmic would be a bad choice. If you are looking to tinker, test and log error reports to help developers and the Karmic teams, go for it.

Running a testing release is not the greatest way to learn Ubuntu (unless you have a LOT of patience) but it IS a good way to get extremely frustrated when things break with the next update. If you don't mind breaking and fixing you are making the right choice. If you actually want to do some productive computing for work or school or whatever, wrong choice. :)

---

