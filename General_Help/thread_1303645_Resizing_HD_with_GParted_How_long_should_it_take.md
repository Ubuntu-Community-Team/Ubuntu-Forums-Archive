---
title: "Resizing HD with GParted: How long should it take?"
date: 2009-10-28
forum: General Help
---

### Post by BCven86 on 2009-10-28
I am trying to resize my hard drive using GParted on the Live cd from 231 GB to 83 GB, but almost a day later it's still going. Is this a normal time length?

I don't want to stop it because I will lose my data. Also, what does it mean when GParted says "Severe damage will be done" if I cancel it. I assume that I would be able to format the hard drive again and everything would be done i.e. I assume "severe damage" doesn't mean hardware damage. Can someone clarify this for me?

Thanks,
Bob

---

### Post by sdowney717 on 2009-10-28
severe data damage not hardware damage.
are you compacting an ntfs partition?
if so did you defrag the partition first?

---

### Post by John Bean on 2009-10-28
> **BCven86 said:**
> I am trying to resize my hard drive using GParted on the Live cd from 231 GB to 83 GB, but almost a day later it's still going. Is this a normal time length?Time is relative but this is longer than I would wait.

>  I don't want to stop it because I will lose my data.You will... probably.

> Also, what does it mean when GParted says "Severe damage will be done" if I cancel it. I assume that I would be able to format the hard drive again and everything would be done i.e. I assume "severe damage" doesn't mean hardware damage.Severe data damage, as in very high probability that no data will survive intact. The hardware will be fine (if it was before, that is).

---

### Post by John Bean on 2009-10-28
> **sdowney717 said:**
> are you compacting an ntfs partition?
if so did you defrag the partition first?Very good point. Maybe leave it a few more days...

---

### Post by BCven86 on 2009-10-28
It's unfortunate that I will lose all my data. The reason I decided to wait so long is that the processor and memory still seem to be running at full strength.

I am resizing an ext3 file system.

---

