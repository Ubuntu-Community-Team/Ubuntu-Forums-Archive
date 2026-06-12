---
title: "Aero-Snap feature without Compiz"
date: 2012-05-27
forum: General Help
---

### Post by jrisreal on 2012-05-27
I've tried to get compiz to work towards my liking, but everytime I solve a problem, a new one comes about.  I've settled on the probability that compiz simply doesn't play nice with xfce/xubuntu.  However, I really like the the aero snap feature.  Is there any way I can implement this without Compiz?  Is there any alternative Window Managers that are Xubuntu-compatible that support this feature?

If a new WM is suggested, please suggest one that is generally more feature-rich than xfwm4, because I don't want to give up any current functionality, solely for that one feature.

Thanks,
    ~Zach

EDIT:  I'd also like to see an implementation of the "negative" feature.  Perhaps there may be a way to get Compiz working in xubuntu after all?  Here are the most problematic things that occurred as a result of compiz:
-At first, whenever I used Compiz, my window theme changed to some generic gtk theme.  I had a customized XFCE Greybird theme that I liked alot, and Compiz rid me of it.  After I managed to fix that issue by changing the theme reference using gconf-editor, I rebooted and as long as I am using Compiz rather than xfwm4, there are no window decorations...doesn't matter if I have window decorations checked or not, the borders are gone.  I also tried changing to Openbox instead, because I heard that some of these features that I want are available on there as well.  Openbox was having trouble with AWN, so I removed it and went back to xfwn4.  I haven't tried fluxbox yet, but I'm still open to any suggestions.

---

### Post by bryncoles on 2012-05-27
Is this what you want?

```
http://www.youtube.com/watch?v=19X0gng_-qk
https://launchpad.net/~fossfreedom/+archive/xfwm4
```

---

### Post by jrisreal on 2012-05-27
> **bryncoles said:**
> Is this what you want?

```
http://www.youtube.com/watch?v=19X0gng_-qk
https://launchpad.net/~fossfreedom/+archive/xfwm4
```
Yes, that's great!  Good answer.

However, I managed to get openBox running well and playing nice with AWN.  Is there any solution for openBox?  Apologies for this switchup, but I think I like openBox better than xfwm4.

If there is no good solution, I'll go ahead and stick with xfwm4 with this patch.

EDIT:  FIXED!!!
I followed this tutorial: [http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/](http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/)
It isn't mouse activated, but I always liked the keybord shortcuts in Aero Snap better than the dragging option.

---

