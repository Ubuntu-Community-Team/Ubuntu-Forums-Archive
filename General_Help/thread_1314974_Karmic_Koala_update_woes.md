---
title: "Karmic Koala update woes"
date: 2009-11-04
forum: General Help
---

### Post by moe_syzlak on 2009-11-04
I updated to Koala with no problems. I thought I was one of those lucky peoples that had a near perfect install. That was until today.

Update Manager started nagging me at boot time to update. So, I said yes. Then later its frozen. The window will not respond. Other Koala updates went fine, but this one is causing me problems. I had no programs running at the time. It was at boot time when all was loaded.

You guys got any suggestions?

---

### Post by hoppipolla on 2009-11-04
Just kill the update manager and update from a prompt :)

```
sudo apt-get update && sudo apt-get upgrade
```

that usually works! Worst comes to the worst you may have to run that command to fix the dependency tree or something but it gives that to you automatically if it is needed I think :)

---

### Post by Tipped OuT on 2009-11-04
All I know is, when I go to Karmic, I'll be doing a fresh install. You guys got me running scared after all of the upgrading horror threads I've seen.

---

### Post by running_rabbit07 on 2009-11-04
> **edin9 said:**
> Seymour Butts?

Very intelligent. Do you have anything useful to add?

---

### Post by running_rabbit07 on 2009-11-04
> **Tipped OuT said:**
> All I know is, when I go to Karmic, I'll be doing a fresh install. You guys got me running scared after all of the upgrading horror threads I've seen.

I did the upgrade using an alternate install disk to get it started. Had no problems.

Edit: I did the upgrade to during the RC period to beat the full release upgrade rush.

---

### Post by hoppipolla on 2009-11-04
> **running_rabbit07 said:**
> I did the upgrade using an alternate install disk to get it started. Had no problems.

I've had no problems either, and I upgraded to the Beta 1 first!

Although my boot up is a little slow.. o.O

---

### Post by PhoHammer on 2009-11-04
> **hoppipolla said:**
> I've had no problems either, and I upgraded to the Beta 1 first!

Although my boot up is a little slow.. o.O

Ditto, boot time and everything.

---

### Post by hoppipolla on 2009-11-04
> **PhoHammer said:**
> Ditto, boot time and everything.

ha! weird man... I wonder what it is...

---

### Post by moe_syzlak on 2009-11-05
OK, the problem was that the window became unresponsive, but the update completed. It worked but it did it in a weird way.

SOLVED.

---

### Post by moe_syzlak on 2009-11-05
Thanks for the help all.

---

