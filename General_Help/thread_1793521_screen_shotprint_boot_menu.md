---
title: "screen shot/print boot menu"
date: 2011-06-29
forum: General Help
---

### Post by soulcat on 2011-06-29
hi

how do i screen shot or print screen boot menu & save to file, tried pressing print screen when booting then paste, would not work, this for a futher question once this one is solved

regards

ubuntu 10.10

---

### Post by smurphy_it on 2011-06-29
If there is no "functionality" built into grub for this, you are pretty much out of luck.  Got a digital camera ?  Perhaps take a picture, and when then paste/copy your picture in :-)

---

### Post by soulcat on 2011-06-29
hi

thought it could not be done will use camera thanx for your reply

regards soulcat

---

### Post by seawolf167 on 2011-06-29
Its not a screenshot - but you can cat the grub menu and read each entry

```
cat /boot/grub/grub.cfg
```or to a file

```
cat /boot/grub/grub.cfg > ~/Desktop/somefile
```

---

