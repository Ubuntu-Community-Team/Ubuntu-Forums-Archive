---
title: "How to get the Ubuntu desktop logo back after installing Kubuntu?"
date: 2011-01-17
forum: General Help
---

### Post by PJOS13 on 2011-01-17
Someone knows how to get the Ubuntu desktop logo back (the one which appears after booting) after installing Kubuntu?

---

### Post by mikewhatever on 2011-01-17
Try this:
```
sudo update-alternatives --config default.plymouth
```

You should get to choose between the two splash screens.

---

### Post by PJOS13 on 2011-01-17
I got this:

```
There are 2 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                     Priority   Status
------------------------------------------------------------
* 0            /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150       auto mode
  1            /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth   150       manual mode
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth     100       manual mode

Press enter to keep the current choice[*], or type selection number:
```

I typed "2" but I'm still getting the kubuntu screen.

---

### Post by PJOS13 on 2011-01-18
How can I configure it?

---

### Post by James78 on 2011-01-18
Check the very last 2 commands at the very end of the tutorial, hopefully that works for you.
[http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

---

### Post by PJOS13 on 2011-01-18
Why did you remove it?

---

### Post by PJOS13 on 2011-01-18
Ok I'll try it. Thank you.

---

### Post by PJOS13 on 2011-01-18
I finally got it, I used the synaptic package manager to remove the plymouth-theme-kubuntu-logo and the plymouth-theme-kubuntu-text. Thank you all.

---

