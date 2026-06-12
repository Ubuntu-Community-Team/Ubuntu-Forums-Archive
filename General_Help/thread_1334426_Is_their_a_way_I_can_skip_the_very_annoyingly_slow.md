---
title: "Is their a way I can skip the very annoyingly slow &quot;read-only test&quot; in GParted?"
date: 2009-11-22
forum: General Help
---

### Post by TheOnlyMrK on 2009-11-22
The title basically says it all, I'm now stuck waiting two and a half hours for GParted to do it's read-only test which is a huge waste of my time. While I know theirs nothing I can do to skip it this time because it's already started, could someone tell me if their is a way to skip the read-only test so I know how to do it next time? Or suggest a completely different partition manager?

---

### Post by dcstar on 2009-11-23
> **TheOnlyMrK said:**
> The title basically says it all, I'm now stuck waiting two and a half hours for GParted to do it's read-only test which is a huge waste of my time. While I know theirs nothing I can do to skip it this time because it's already started, could someone tell me if their is a way to skip the read-only test so I know how to do it next time? Or suggest a completely different partition manager?

By the sound of it gparted is doing a full sector read of the drive, I believe that it would only do this either by request or if the drive had problems that caused a full surface read to verify that it is actually usable.

---

### Post by TheOnlyMrK on 2009-11-23
> **dcstar said:**
> By the sound of it gparted is doing a full sector read of the drive, I believe that it would only do this either by request or if the drive had problems that caused a full surface read to verify that it is actually usable.
It does it every time I resize a partition no matter what hard drive or computer I'm on. Only reason it became a *huge* annoyance to me now is because I had to shrink a partition with almost 200GiB of stuff to make room for a new 250GiB partition at the beginning of the drive (1TiB drive) so it took a very long time, two and a half hours for the "read-only test" and a lil over six hours for the actual thing, That's almost half a day.

---

### Post by wilee-nilee on 2009-11-23
It is frustrating but whatever you do don't stop it, I borked a HD that way that was rather worn anyway but gparted wont read it anymore.

---

### Post by TheOnlyMrK on 2009-11-23
> **wilee-nilee said:**
> It is frustrating but whatever you do don't stop it, I borked a HD that way that was rather worn anyway but gparted wont read it anymore.
Well if you still have/care about the hard drive I'd suggest trying DBAN. It's saved alot of my hard drives plus a few of my friends hard drives, and actually made them a few GiB bigger a couple times. [http://www.dban.org/](http://www.dban.org/) I just use the "Quick Erase" which just fills the hard drive with zero's. Though ofcoarse this will wipe the drive completly just to warn anyone else that thinks about trying this.

---

