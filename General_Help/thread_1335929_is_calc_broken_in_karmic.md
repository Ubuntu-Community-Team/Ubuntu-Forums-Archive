---
title: "is calc broken in karmic?"
date: 2009-11-24
forum: General Help
---

### Post by hardyn on 2009-11-24
trying to do a negative exponent.  positive seem to work fine.  the following is from the gcalc help:

12exp+8 = 1200000000

12exp-8 = 24.619381941509

or is there a special way the -ve must be used... or im clearly missing something.

thanks.

found this:

"2. We fill fix the negative exponents issue in the next release, sorry
for that.
btw, for time, you can always enter 1e-12 like, 12, +/- (gives -12),
check the inv flag, and click Log, forming 10^-12. 
"

this post was 2006... maybe we should get on this gnome people?

---

### Post by Arand on 2009-11-24
Seems to be a mixup in the Karmic version:
2e+2 is interpreted as 2*10^2
Whereas
2e-2 is interpreted as (2*e)-2, where e is Euler's constant

In the Lucid version e has shifted over to exclusively mean Euler's constant, so it seems like the Karmic version got caught mid-transition somehow.

Oh, and by the way, already reported: [https://bugs.launchpad.net/ubuntu/+source/gcalctool/+bug/483730](https://bugs.launchpad.net/ubuntu/+source/gcalctool/+bug/483730)


- Arand

---

