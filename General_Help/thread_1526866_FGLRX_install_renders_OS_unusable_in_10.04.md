---
title: "FGLRX install renders OS unusable in 10.04"
date: 2010-07-08
forum: General Help
---

### Post by rickgg on 2010-07-08
the "x" to close windows disappeared on everything except google chrome, my keyboard stops registering in text fields randomly, I cannot move any window but for chrome, Alt+TAB does not work, and the graphics just to use the desktop are excruciatingly laggy.  It was so bad I had to restart the computer and boot into Windows just to type this..... and I restarted back into Kubuntu several times hoping it would fix it, but it didn't.

my computer specs are in my signature, and I could really use some help with this....

---

### Post by QIII on 2010-07-08
How did you install the driver?

Did you issue

```
aticonfig  --initial
```?

I have seen some discussion about driver issues with regard to the HD 4890 series using the proprietary driver.  It might be worth taking a look at Launchpad to see if there has been any resolution


Edit:  Just looked at your bean count and realized you may not be familiar with Launchpad.  Easiest way for you too look might be to google

```
site:launchpad.net "HD 4890"
```

If I get a chance a little later, I'll see what I can find for you.

---

### Post by rickgg on 2010-07-08
I used that command, and it appeared to work.  However, upon restarting my computer, it gave the aforementioned results.  I too have seen people have issues with my card and most direct derivatives of Unix.  I have seen posts on Mac forums reporting issues as well (I am the techie among my friends, and they always ask me for help with computers; and I am about to take my A+ exams).  I'm beginning to wonder if I should stay away from  Linux until I upgrade my card, or until support is given to my card, which ever comes first.  the 4890 seems to be a curse for anything other than Faildows....

I will check out launchpad, as recommended...

thx

---

### Post by QIII on 2010-07-08
Rather than not using Linux at all, you could remove the fglrx driver and depend on the open source one.

That wouldn't give you some of the nice features (3D, multiple screens, effects, etc), but you could still use and learn Linux.

I think there are a lot of people shaking their fists at AMD/ATI on this one.

---

