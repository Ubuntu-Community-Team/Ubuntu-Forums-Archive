---
title: "Ubuntu 10.04 Sound is low if I start my computer with headphones.."
date: 2010-05-05
forum: General Help
---

### Post by QueenZ on 2010-05-05
So my sound volume is very low if i start my computer up when i have headphones plugged in even when all volume controls are up to 100% but when i start it without headphones plugged in it is loud and normal. What could be the problem?

Using Toshiba Laptop with Ubuntu 10.04 Lucid Lynx

---

### Post by viralmeme on 2010-05-05
> **QueenZ said:**
> So my sound volume is very low if i start my computer up when i have headphones plugged in even when all volume controls are up to 100% but when i start it without headphones plugged in it is loud and normal. What could be the problem?

Using Toshiba Laptop with Ubuntu 10.04 Lucid Lynx

Try running alsamixer..

$alsamixer
$alsactl store

---

### Post by wika on 2010-05-15
Thank you !!!

that was exactly what i was looking for !!

:)

---

### Post by noletolucas on 2011-07-03
thanks!

right. i had the same issue. somehow after the upgrade the "speaker" volume was set to minimum.

---

