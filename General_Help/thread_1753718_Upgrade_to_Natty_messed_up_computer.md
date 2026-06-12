---
title: "Upgrade to Natty messed up computer"
date: 2011-05-09
forum: General Help
---

### Post by runner72 on 2011-05-09
Hello all,
Yesterday for Mother's Day I got wireless printing working on my mom's computer... Then when I upgraded the laptop to 11.04 it wouldn't boot properly. It shows the Ubuntu splash and then switches to a console where I can see services starting and stopping. It freezes when it's going through this section of startup. I rebooted and started the machine in recovery mode, then selected low-graphics from the list. It works in low-graphics mode in Ubuntu Classic (my mom doesn't want Unity so I set Classic as the default). How can I get it to boot normally?

---

### Post by matt_symes on 2011-05-09
Hi

Can her computer run unity ? From a terminal in low graphics mode or the console type

```
/usr/lib/nux/unity_support_test -p
```

Kind regards

---

### Post by runner72 on 2011-05-09
I don't think it works with Unity... when I switched to low graphics mode it told me that I couldn't use Unity and that I had to switch to Classic. No big deal because we wanted Classic anyways.

Here's the output:

```
beth@beth-laptop:~$ /usr/lib/nux/unity_support_test -p
Segmentation fault
```

---

### Post by matt_symes on 2011-05-09
Hi
[FONT=monospace]
[/FONT]> beth@beth-laptop:~$ /usr/lib/nux/unity_support_test -p 
Segmentation faultThat would be a problem. Are you still getting the freeze issue in Classic ?

Kind regards

---

### Post by runner72 on 2011-05-09
Yes... Even though I set the default to Classic, when I try to reboot it and it's not in low-graphics mode, it hangs on the same spot. I can still access the terminals; I tried a [FONT=Courier New]startx[/FONT] but that didn't work. I can only get to the desktop in low graphics mode.

---

### Post by runner72 on 2011-05-09
It was a drivers issue! I went into Additional Drivers and enabled a graphics driver... That fixed everything and I was able to boot no problem!
I'm going to mark this thread as solved. Thank you so much for your help!

---

