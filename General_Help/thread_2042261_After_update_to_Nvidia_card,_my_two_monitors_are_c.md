---
title: "After update to Nvidia card, my two monitors are considered 1"
date: 2012-08-14
forum: General Help
---

### Post by timetopat on 2012-08-14
After someone said that my ati card could be the cause of some of my video problems, I went out and found a relatively inexpensive nvidia card.  After purging the ATI card from the system , and installing the nvidia card and the recommended proprietary drivers, I was back to normal with now functioning flash and other products working 100 percent better.

My problem is I have 2 monitors connected and in the setup that closest matches my ATI setup, the Computer thinks the screen resolution is 1 monitor with 3500 Pixels by 1080 pixel. Some games I have default to this resolution and stay there.

Is there any way for this to not happen and have the computer recognize them as 2 separate monitors?  

Thanks

---

### Post by ianhaycox on 2012-08-15
Try running,

```
$ nvidia-settings
```

and you can choose the type of dual monitor configuration.

---

