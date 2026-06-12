---
title: "Hard drive sector problem"
date: 2012-08-06
forum: General Help
---

### Post by williammanda on 2012-08-06
I have a hard drive that keeps unmounting but can be remounted after a restart. The only consistancey is seems is that when the drive is accessed for some files it unmounts. The smartdata says it has 19 bad sectors (see attached photo). Is there a way to mark the bad sectors while not damaging the data on the drive?

---

### Post by Mark Phelps on 2012-08-06
Don't want to be an alarmist -- but that is the SAME model WD drive that started failing on me after a few months.

If you can connect that drive to a Windows PC, WD provides a downloadable diagnostic app you can run on the drive to detect and (possibly) fix filesystem problems.

---

### Post by dcstar on 2012-08-08
> **williammanda said:**
> I have a hard drive that keeps unmounting but can be remounted after a restart. The only consistancey is seems is that when the drive is accessed for some files it unmounts. The smartdata says it has 19 bad sectors (see attached photo). Is there a way to mark the bad sectors while not damaging the data on the drive?

```
man badblocks
```

Read the stuff about using the other tools.

---

