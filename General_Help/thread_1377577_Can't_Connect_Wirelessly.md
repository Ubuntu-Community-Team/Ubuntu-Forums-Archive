---
title: "Can't Connect Wirelessly"
date: 2010-01-10
forum: General Help
---

### Post by Hman242 on 2010-01-10
I have just put Ubuntu Studio on my laptop, and I can't get the internet to work. I have a feeling that it has something to do with my button thats toggles the power of my wireless device being red all the time. If i press it, it stays red. I tried to install NDISwrapper, but it says it can't find the package. Please help :(

---

### Post by Greenwidth on 2010-01-10
What make/model is your wireless card?
Type 'lspci' into a termial and post the output here.

You could also try connecting wired and seeing if there is a driver to enable in:
System > Admin > Hardware Drivers

---

### Post by Hman242 on 2010-01-10
Broadcom Corp. BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

---

### Post by Greenwidth on 2010-01-10
The STA driver for this is:
[http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

Easiest way to install it is either connecting wired, or put the LiveCD in and add it as a source in:
System > Admin > Software Sources

Then check in:
System > Admin > Hardware Drivers
for a driver to install.

---

### Post by Hman242 on 2010-01-10
Sorry for being such a newbie, but could you walk me through installing that through the LiveCD?

---

### Post by lotharmat on 2010-01-10
> **Hman242 said:**
> Sorry for being such a newbie, but could you walk me through installing that through the LiveCD?


Don't apologise for being a n00b! - We were all there (I still am)

basically:

Put the Live CD ( that you probably installed ubuntu from) in
click System --> Administration --> Software sources
Type in your password
Put a tick in the box called Installable from CD ROM (attached Picture)
Then - click System --> Administration --> Hardware devices; see if the card shows up in this

---

### Post by Hman242 on 2010-01-10
The disc shows up twice named with the same name, does it matter which one? Also, I'm guessing that you press Revert after you select it?

---

### Post by Hman242 on 2010-01-10
Bump.

---

### Post by warfacegod on 2010-01-10
Just on a lark. Go to System> Admin.> Hardware Drivers and see if there is a recommended wireless driver and that it is activated.

---

### Post by Hman242 on 2010-01-10
Nothing comes up when I go into Hardware Drivers.

---

### Post by warfacegod on 2010-01-10
> **Hman242 said:**
> The disc shows up twice named with the same name, does it matter which one? Also, I'm guessing that you press Revert after you select it?

Sure try 'em both. No, revert will set it to default settings, just click close. It'll ask to reload, do it.

---

### Post by Hman242 on 2010-01-10
I completely reinstalled my OS, and now two wireless drivers show in Hardware Drivers. I activated them & they worked just fine.

---

### Post by warfacegod on 2010-01-10
You have two wireless cards? Other wise there should only be one active driver. Preferably the recommended one. Oh well, whatever.

---

### Post by Greenwidth on 2010-01-10
Maybe the STA and the B43 ones..?

---

