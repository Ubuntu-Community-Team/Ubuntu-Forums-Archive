---
title: "xubuntu not booting with newer kernels"
date: 2011-05-25
forum: General Help
---

### Post by jerry_c on 2011-05-25
Here's my problem:

I can boot xubuntu fine in kernel 2.6.32.25, but nothing newer. When I try to boot in a later kernel, I get a bunch of scrolling text, followed by a text based login prompt that doesn't work.

I've been running xubuntu on this computer since version 8.04. I've had this problem since I upgraded to version 10.04. I figured an update would fix it, so I just made do. I figured for sure when the next upgrade came out it would be fixed, but I upgraded to 11.04 and still have the same problem. I figured somebody else would have had this problem by now and posted a solution, but I haven't found one, either on this forum or even on a google search.

It's an old compaq with 236 megs of memory.

I just noticed that, while ubuntu used to require at least 256 megs of memory, and xubuntu was for older computers with as few as 192, I believe, xubuntu now requires 256. Is that my problem? Should I be looking at a different distro now?

Any ideas?

Thanks.

---

### Post by 3Miro on 2011-05-25
256MB is low, but Xubuntu should work well enough on it.

What is your video card? If you are using a proprietary driver, it probably got broken during the update, proprietary drivers do that sometimes. If you can boot into the system with any kernel, you can try to reinstall the video driver (go to Additional Drivers, disable the drivers, reboot, enable the driver, reboot).

Let me know if this doesn't help.

---

### Post by novinick on 2011-05-25
hi 
perhaps is not possible to do miracles :(
hardware is too old for new kernel :redface:

---

### Post by jerry_c on 2011-05-25
> **3Miro said:**
> 256MB is low, but Xubuntu should work well enough on it.

I only have 236.

> **3Miro said:**
> What is your video card? If you are using a proprietary driver, it probably got broken during the update, proprietary drivers do that sometimes. If you can boot into the system with any kernel, you can try to reinstall the video driver (go to Additional Drivers, disable the drivers, reboot, enable the driver, reboot).

Let me know if this doesn't help.

I tried this. It said that there are no proprietary drivers in use.

Thanks for your help.

---

### Post by jerry_c on 2011-05-25
> **novinick said:**
> hi 
perhaps is not possible to do miracles :(
hardware is too old for new kernel :redface:

So, some questions come to mind:
[LIST=1]
[*]Do I run any security risk running the older kernel?
[*]Should I move to another distro now that xubuntu has upped its requirements?
[*]If so, which one?
[/LIST]

Thanks for your help.

---

### Post by 3Miro on 2011-05-25
Without prop drivers, the video shouldn't be broken, although it is hard to tell on old video cards.

- running an older kernel is a potential security risk, but not too big
- 236 or 256 is about the same. Remove some applets that you are not using, disable composition and Xubuntu should work.
- The only other distro that can potentially be smaller is Lubuntu, although its environment is still work in progress and in my experience is somewhat buggy.
- You can try to setup a standalone windows manager like OpenBox. 
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
You can do that on your current Xubuntu installation. Things don't get lighter than a standalone OpenBox.

---

### Post by jerry_c on 2011-05-27
The person who uses this computer likes the taskbar, desktop, etc., so something like openbox won't do.

I'll try reducing what loads at startup, if I can figure out how do to that, and see if that helps.

With the old kernel, it'll even run firefox, gimp, and openoffice at the same time. It's just getting it to boot to the gui, which I think is xfce.

Thanks for your help.

---

