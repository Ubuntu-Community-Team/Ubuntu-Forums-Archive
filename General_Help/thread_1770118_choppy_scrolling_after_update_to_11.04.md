---
title: "choppy scrolling after update to 11.04"
date: 2011-05-28
forum: General Help
---

### Post by nethero on 2011-05-28
As the title says, scrolling is choppy after I've updated.  I suspect my video driver is to blame.  I went to System > Administration > Additional Drivers and saw that it was "Activated but not currently in use".  How do I fix this?

---

### Post by wildmanne39 on 2011-05-28
> **nethero said:**
> As the title says, scrolling is choppy after I've updated.  I suspect my video driver is to blame.  I went to System > Administration > Additional Drivers and saw that it was "Activated but not currently in use".  How do I fix this?
Hi, that is just a bug it really is in use. Have you enabled the cube or desktop effects? that caused mine to do the same thing, I had to change a lot of settings to make it work right. Also if there is 2 drivers in the additional drivers install the other one and see it that fixes it.

---

### Post by nethero on 2011-05-29
Ah okay,

I made the mistake of posting my problem before troubleshooting/searching thoroughly.  Yes, this appears to be a bug.  All I did was restart my computer and the choppy scrolling went away.  In the Additional Drivers section, it still says that the driver is "Activated but not currently in use".  However when I run lspci -v I can see that my video card is using nvidia-173, nvidia-current etc. etc.

Yes, I had enabled some of the compiz options, but not the cube.  Anyway, it appears to be working properly now.  Thanks!

---

### Post by wildmanne39 on 2011-05-29
> **nethero said:**
> Ah okay,

I made the mistake of posting my problem before troubleshooting/searching thoroughly.  Yes, this appears to be a bug.  All I did was restart my computer and the choppy scrolling went away.  In the Additional Drivers section, it still says that the driver is "Activated but not currently in use".  However when I run lspci -v I can see that my video card is using nvidia-173, nvidia-current etc. etc.

Yes, I had enabled some of the compiz options, but not the cube.  Anyway, it appears to be working properly now.  Thanks!
Hi, your welcome, if you want to enable effects in natty you need to follow this guide. [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html) but it still takes tweaking of some settings that the guide does not cover. Would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

