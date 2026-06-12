---
title: "Jaunty freezes after loading bar"
date: 2009-07-09
forum: General Help
---

### Post by kogger on 2009-07-09
I've recently had some problems getting grub to let me back into my computer after a failed attempt to upgrade it, but I seem to almost have it fixed. It did let me boot into ubuntu, but it showed a bunch of scrawling text instead of the loading bar, so I ended up booting into recovery mode and overwriting my menu.lst file with the provided one, so then I can make my personal adjustments to it after the booting process returns to normal.

I can now boot into grub with the default menu, and I can start booting into ubuntu. The loading bar comes, loads, then disappears; and then it freezes. It flashes some distorted graphics (including the ubuntu logo) a couple times, and then it settles on displaying them permanently. Sometimes my computer makes a few more noises, but ultimately it does nothing and won't finish booting. Right now I can only guess that it has something to do with my wireless driver.

Any suggestions?

---

### Post by kogger on 2009-07-09
I've tried uninstalling a wireless driver, disabling wireless on my laptop, and fixing broken packages through recovery mode, but it keeps freezing and won't let me boot.

---

### Post by Legace on 2009-07-10
Do you happen to have a ATi graphics chip and did you happen to install the ATi drivers?

---

### Post by kogger on 2009-07-10
I think I have Nvidia, but I don't know the details on that.

---

### Post by kogger on 2009-07-10
Well, I got it to boot by following [this page](https://help.ubuntu.com/community/RadeonDriver) and uninstalling my fglrx driver. Now to check for consistency, but I think it will work now. =)

---

