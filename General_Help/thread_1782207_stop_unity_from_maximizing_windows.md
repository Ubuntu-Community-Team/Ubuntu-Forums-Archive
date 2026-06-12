---
title: "stop unity from maximizing windows"
date: 2011-06-14
forum: General Help
---

### Post by jworr on 2011-06-14
Unity always maximizes firefox when I open it, is there a way to turn this off?

---

### Post by coffeecat on 2011-06-14
If it's unmaximised to a size greater than about 75% of a maximised window, it will open maximised when next opened. You need to reduce the size of the unmaximised window to less than this threshold. I'm guessing it's 75% but even if not, it's near that figure. A bit of trial and error should find you a compromise between a firefox window large enough to be usable, but not too large that it exceeds the threshold.

Except on very small screens when you're better off with a maximised firefox anyway.

---

### Post by jworr on 2011-06-14
do you mean I just need to make the window smaller before I close it?  Is there any way to make windows open to the same size they were previously?

---

### Post by coffeecat on 2011-06-14
Yes. I mean to make the window a bit smaller before you close it. But you don't  need to make the window smaller every time you close it. You should be able to find a size that is small enough to re-open the same size, and which is large enough to be usable. Even on my 15" laptop, a non-maximised window small enough to open the same size when re-opened is quite large enough to be usable. Only on my 10" netbook do I not use a maximised firefox all the top because a non-maximised on such a small screen would be pointless.

---

### Post by mc4man on 2011-06-14
The 75% is coded into unity, atm can only be changed by re-building the source. (I use 90% here, simple change and build
There were some reasons for this behavior although the % was somewhat arbitrarily chosen (i suggested it, sorry if too low, seemed reasonable

There has been a commit approved and merged into unity that is going to create a config option to set to % of choice, 1 > 100.
Whether it makes it into a natty unity update is unclear, it will certainly be in the 11.10 unity

---

