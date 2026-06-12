---
title: "Nautilus lags waiting for external drive to spin up every time I change folders."
date: 2009-07-08
forum: General Help
---

### Post by u-slayer on 2009-07-08
I have an external hard drive connected to my computer. After a certain amount of time it automatically spins down.

When I click on any folder in nautilus, I have to wait for the drive to spin up, before I can do anything. This becomes extremely annoying, so much so that I have to unmount the external drive to stop nautilus from spinning it up all the time. Is there any one to fix this?

---

### Post by michy99 on 2009-07-08
I have the same situation. The only solution I have found so far is to turn it off when I am not using it.

---

### Post by Jebtrix on 2009-07-08
Try 
```
gksudo gedit /etc/hdparm.conf
```

Uncomment and change:
```
#spindown_time = 24 

to

spindown_time = 0
```

---

### Post by Jebtrix on 2009-07-08
Never really paid much attention but some BIOSs got spindown rules that may or may not supercede acpi/OS.. just never checked

---

### Post by u-slayer on 2009-07-08
> **Jebtrix said:**
> Try 
```
gksudo gedit /etc/hdparm.conf
```

Uncomment and change:
```
#spindown_time = 24 

to

spindown_time = 0
```

1. It's not the OS that spins down the HDD. The drive itself has firmware to tell it to do that.

2. There's nothing wrong with spinning down. But, I shouldn't have to wait for it to spin up when I'm not even accessing a folder on the drive that is spinning up.

Changing folders in the terminal doesn't make the drive spin up. But nautilus does. This is a bug in nautilus.

---

### Post by Jebtrix on 2009-07-08
Ahh, IC my bad... thats a concrete case of SOL

---

### Post by u-slayer on 2009-07-08
> **Jebtrix said:**
> Ahh, IC my bad... thats a concrete case of SOL

That's not very helpful.

---

### Post by Jebtrix on 2009-07-08
If its firmware, there isn't nothing do but check manufacturer.. which is almost always a SOL. If the enclosure has some firmware/controller, you could just use a generic one and reuse the drive itself.

---

### Post by u-slayer on 2009-07-08
> **Jebtrix said:**
> If its firmware, there isn't nothing do but check manufacturer.. which is almost always a SOL. If the enclosure has some firmware/controller, you could just use a generic one and reuse the drive itself.

Or someone could actually fix this bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/376053](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/376053)

---

### Post by Jebtrix on 2009-07-08
Just curious is yours a cryptsetup LUKS disk also?

---

### Post by u-slayer on 2009-07-08
> **Jebtrix said:**
> Just curious is yours a cryptsetup LUKS disk also?

I use cryptsetup, but not the LUKS extension. What makes you ask? The external drive is truecrypt.

---

### Post by Jebtrix on 2009-07-08
I read the bugreport link you posted and was just seeing if that was indeed a common denominator.

I read about this awhile ago but it seems somewhat related, or maybe a regression caused by trying to address it (just thinkin out loud on this):

[https://bugs.launchpad.net/ubuntu/+bug/117713](https://bugs.launchpad.net/ubuntu/+bug/117713)

---

### Post by u-slayer on 2009-07-11
bump

---

### Post by davidY on 2009-12-05
Try mounting it under /media

It doesn't spin up anymore (hint: cds don't spin up when you access your folders)

---

