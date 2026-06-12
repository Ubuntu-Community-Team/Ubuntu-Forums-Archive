---
title: "ATI 9600 Mobility Radeon - Any Tweaks for Natty?"
date: 2011-04-29
forum: General Help
---

### Post by crjackson on 2011-04-29
I haven't been around for much of the natty testing cycle, but now that it's released, I was hoping someone could help with getting a little better performance out of the open driver for my ATI 9600 video.

This is an older lappy (about 7 years old) with a 2GHz AMD 64 processor.

Natty is configured to boot into the classic GDE with no effects turned on. It's painfully slow and I was hoping that some one could help me crank up the performance a little. This thing used to fly on older versions after the ATI proprietary driver was installed, but this card isn't supported by ATI any more.

Thanks for any help...

---

### Post by crjackson on 2011-04-29
I'm sitting here in the hospital hoping some one can sneak me a tweak or two so the time will pass.

---

### Post by crjackson on 2011-05-03
bump

---

### Post by clhsharky on 2011-05-04
crjackson

Hope your doing well.

If your not getting Software Rasterizer or AGP issues, xorg-edgers is probably best you can do in Natty. The OSS R300G driver is working well for me in Natty.

xorg-edgers
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)


Sharky

---

### Post by crjackson on 2011-05-06
> **clhsharky said:**
> crjackson

Hope your doing well.

If your not getting Software Rasterizer or AGP issues, xorg-edgers is probably best you can do in Natty. The OSS R300G driver is working well for me in Natty.

xorg-edgers
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)


Sharky

Thanks, I'm still hanging on and kicking hard.

I'm using that repo already, I just can't get any POP! out of the video on natty. It's too bad that ATI dumped support for this adapter, It's a really fast lappy on older versions, but I've had to tweak the last 3 releases (with help from others) to get it flowing. The tweaks from other versions of Xorg.conf just seem to never carry over from previous to latest.

---

### Post by vanquishedangel on 2011-05-06
> **crjackson said:**
> Thanks, I'm still hanging on and kicking hard.

I'm using that repo already, I just can't get any POP! out of the video on natty. It's too bad that ATI dumped support for this adapter, It's a really fast lappy on older versions, but I've had to tweak the last 3 releases (with help from others) to get it flowing. The tweaks from other versions of Xorg.conf just seem to never carry over from previous to latest.

Well this maybe late and out of the question but have you considered using lubuntu from the repositories? If you boot into LXDE at start up it looks good and it is realy, really light on system resources leaving more for graphics and other applications and it is really snappy, you also have all the functions that you have in a normal ubuntu desktop, when prompted I choose LXDM. One of my computers, a Compaq presario 1.6ghz processor, 1 gig ram, ATI mobility Radeon 7500, does quite well with it and it is over 10 yrs old and runs like new.

---

### Post by crjackson on 2011-05-07
> **vanquishedangel said:**
> Well this maybe late and out of the question but have you considered using lubuntu from the repositories? If you boot into LXDE at start up it looks good and it is realy, really light on system resources leaving more for graphics and other applications and it is really snappy, you also have all the functions that you have in a normal ubuntu desktop, when prompted I choose LXDM. One of my computers, a Compaq presario 1.6ghz processor, 1 gig ram, ATI mobility Radeon 7500, does quite well with it and it is over 10 yrs old and runs like new.

I might give that a go, but it doesn't really accelerate the video output in FPS. That's just a light on it's feet desktop that doesn't need many FPS for IT'S use. Thus, not really helping the apps. that need the video horsepower.

---

