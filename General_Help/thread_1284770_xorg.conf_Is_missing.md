---
title: "xorg.conf Is missing"
date: 2009-10-07
forum: General Help
---

### Post by PostChache on 2009-10-07
Well, I'm using Radeon HD Open-Source driver and I was going to go tweak some of my settings in xorg.conf and it's empty O.O So I didn't think big of it I thought maybe if it was just blank that it'd be all defaults so I continue with some changes and it says that it can't save because xorg.conf doesn't exist. Is there anyway to restore it.

---

### Post by plucky on 2009-10-07
> **PostChache said:**
> Well, I'm using Radeon HD Open-Source driver and I was going to go tweak some of my settings in xorg.conf and it's empty O.O So I didn't think big of it I thought maybe if it was just blank that it'd be all defaults so I continue with some changes and it says that it can't save because xorg.conf doesn't exist. Is there anyway to restore it.

Are you sure you are looking in the right place?

Open a terminal and input ```
locate xorg.conf
``` and see what that gives you.

Or ```
cd /etc/X11/
ls -l
``` The X has to be uppercase and the L is lowercase.

The command to generate another xorg.conf is ```
sudo dpkg-reconfigure xserver-xorg
```


Good Luck

---

### Post by PostChache on 2009-10-07
> **plucky said:**
> Are you sure you are looking in the right place?

Open a terminal and input ```
locate xorg.conf
``` and see what that gives you.

Or ```
cd /etc/X11/
ls -l
``` The X has to be uppercase and the L is lowercase.

The command to generate another xorg.conf is ```
sudo dpkg-reconfigure xserver-xorg
```
Good Luck

Okay that worked xD Thankyou

---

