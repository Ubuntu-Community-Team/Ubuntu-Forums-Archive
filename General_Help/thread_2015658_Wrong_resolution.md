---
title: "Wrong resolution"
date: 2012-07-03
forum: General Help
---

### Post by Blasphemous on 2012-07-03
After installing the the proper Nvidia **proprietary driver** for my GeForce 7025 **I can't get to set the right resolution**: is should be way higher.
With open driver I never had this problem.

The only tool I can use to adjust the screen settings is the Nvidia one, and here's a screenshot:
[U][I][B][IMG]http://i49.tinypic.com/u3nk2.jpg[/IMG]

[/B][/I][/U][LEFT]In fact, there's a way to enter a costum resolution, but I just can't remember the one I was using before I had this issue!

I'm using Ubuntu **10.04** 64 bit (but I've been experiencing this problem even in 12.04).[/LEFT]

---

### Post by flipper T on 2012-07-03
if it was working ok before enabling proprietary driver, disable that driver & reboot

...happy days are here again...

---

### Post by Blasphemous on 2012-07-04
Man, that's some brilliant response!
With closed driver I gained a lot in terms of stability, power usage and fastness of the whole system.
The only issue is the resolution...

---

### Post by cortman on 2012-07-04
What is the output of

```
xrandr
```

---

### Post by msammels on 2012-07-04
Also, what version of the restricted drivers? Current or new?

---

### Post by matt_symes on 2012-07-04
Hi

What resolution are you looking for Blasphemous?

You use xrandr to create and add custom resolutions.

Do you have an old xorg.conf ?

Kind regards

---

### Post by flipper T on 2012-07-04
> **Blasphemous said:**
> Man, that's some brilliant response!
With closed driver I gained a lot in terms of stability, power usage and fastness of the whole system.
The only issue is the resolution...

didn´t you say that resolution used to be ok before you installed driver ?

¨With open driver I never had this problem¨

---

### Post by Grenage on 2012-07-04
> **Blasphemous said:**
> After installing the the proper Nvidia **proprietary driver** for my GeForce 7025 **I can't get to set the right resolution**: is should be way higher.
With open driver I never had this problem.

The only tool I can use to adjust the screen settings is the Nvidia one, and here's a screenshot:
[U][I][B][IMG]http://i49.tinypic.com/u3nk2.jpg[/IMG]

[/B][/I][/U][LEFT]In fact, there's a way to enter a costum resolution, but I just can't remember the one I was using before I had this issue!

I'm using Ubuntu **10.04** 64 bit (but I've been experiencing this problem even in 12.04).[/LEFT]

Unless something has changed, the proprietary driver uses xorg.conf for configuration.  It's easy enough to add a custom resolution, but the problem may just stem from bad EDID data; I've no idea why that wouldn't occur with the open driver.

If you know your monitor specs, you can add those to the xorg.conf.  If you get stuck, you can post your info here, and we can help.  The info we'd need is:

A copy of your /etc/X11/xorg.conf.
Your monitor make and model.
Your GFX model (lspci | grep -VGA).

Rough guide [here]("http://www.grenage.com/xorg.html").

---

