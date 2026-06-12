---
title: "soft lockup bug - cannot boot into Ubuntu at all"
date: 2011-07-30
forum: General Help
---

### Post by Idefix82 on 2011-07-30
Suddenly, as of today, I cannot boot into Ubuntu at all. I have two kernels installed, 2.6.35-28 and 2.6.35-30. The first thing that happened today was that I wasn't able to boot into the latter. I was shown the (in)famous "BUG: soft lockup - CPU#0 stuck for 61s". At this point I could still boot into the 2.6.35-28 kernel. But after shutting down and starting again an hour later, I got the same message when trying to boot into 2.6.35-28. I have tried leaving out the boot options "splash" and "quiet" on both kernels and also adding in "noapic". No combination helps. Needless to say, booting into recovery mode doesn't work either. Up until today, I have been able to boot into both kernels with no problems.

I am typing this under Windows on the same machine. Any pointers to possible solutions will be greatly appreciated!

---

### Post by Idefix82 on 2011-07-30
A brief update: Ubuntu has now booted into 2.6.35-30. I wish I could prevent this bug from happening again though. So any ideas will still be gratefully received.

---

