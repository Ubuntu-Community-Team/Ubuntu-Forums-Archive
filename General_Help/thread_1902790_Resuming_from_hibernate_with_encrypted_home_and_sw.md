---
title: "Resuming from hibernate with encrypted home and swap"
date: 2011-12-31
forum: General Help
---

### Post by Iceman71 on 2011-12-31
Hi,

After reading lots of threads I think I've realized that encrypting my home directory makes resuming from hibernate impossible. Is this considered a bug or is it just a fact with no solution to be expected?
(This concerns my Ubuntu 11.10 installation.)

Regards
Iceman71

---

### Post by Paddy Landau on 2012-01-01
It is just a fact.

When you hibernate, the state of the machine is saved to swap. As swap is (correctly) encrypted, it makes it impossible to read it in order to resume.

There may be a way in future to allow it to resume by entering your password to allow the swap to be read, but that would require further development.

---

### Post by 2F4U on 2012-01-01
This has nothing to do with Ubuntu and is, as far as I know, the expected behaviour on every Linux distribution.

---

### Post by Homie Bongo on 2012-01-01
Of course it is a bug. We can debate and try to understand where the problem lies, but as long as Ubuntu wants to be an easy to understand OS, it should either ask for the password on the wake-up or not offer the hibernate option in the menu at all.

---

### Post by Paddy Landau on 2012-01-01
> **Homie Bongo said:**
> Of course it is a bug.
You have a point. Perhaps you can raise a bug?

> **Homie Bongo said:**
> ... it should either ask for the password on the wake-up or not offer the hibernate option in the menu at all.
Good point. Disable the hibernate option when the swap is encrypted, until such time as the Linux people have figured out a solution. I have raised a [Brainstorm for hibernation and encryption]("http://brainstorm.ubuntu.com/idea/29055/"); if it is approved, add your votes for or against, or add your own solution.

---

### Post by Iceman71 on 2012-01-01
Hi,

Well, I would definitely have preferred the "pointsec approach" to the problem where I have to use two passwords to resume after hibernate (pointsec and windows/linux pwd). As I'm a big fan of the hibernate feature, I really hope that the Linux experts change this so that hibernate can be used on installations with encrypted home directories in the near future.

I think there is a lack of understanding on this topic, as there are many threads in different forums discussing these problems and whether or not a workaround is compatible with their respective hardware. It may very well be this problem that is the reason for users having different experience from the workarounds suggested and not the specific hardware.

Thanks and regards!
Iceman71

---

### Post by Paddy Landau on 2012-05-25
I have written a how-to for [hibernation with encryption]("http://ubuntuforums.org/showthread.php?t=1986821"). I hope it helps.

---

