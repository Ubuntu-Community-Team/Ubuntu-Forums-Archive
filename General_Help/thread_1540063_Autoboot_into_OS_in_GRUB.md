---
title: "Autoboot into OS in GRUB"
date: 2010-07-27
forum: General Help
---

### Post by Vapourstreak on 2010-07-27
Hey, I have only Ubuntu installed, but somehow, the GRUB menu somehows shows up everytime I boot.  Is there a way to make it autoboot into Ubuntu?

---

### Post by VH-BIL on 2010-07-27
install the startupmanager package and set the time to 0 seconds.

---

### Post by TheStroj on 2010-07-27
You can also edit grub file and set timeout to 0.
```
nano /etc/default/grub
```

save it, after that run:

```
update-grub
```

should do same as above post :)

---

### Post by VH-BIL on 2010-07-27
@TheStroj
I like your signature!

---

### Post by Vapourstreak on 2010-07-27
Does the startup manager do the same thing as setting the timeout to zero?  I tried setting it to zero and it gave me a timeout error before booting.  Is there a way to get rid of it?

---

### Post by VH-BIL on 2010-07-27
the startupmanager is just GUI for grub, usplash and
splash screens

---

### Post by TheStroj on 2010-07-27
> **Vapourstreak said:**
> Does the startup manager do the same thing as setting the timeout to zero?  I tried setting it to zero and it gave me a timeout error before booting.  Is there a way to get rid of it?

Set timeout back to something thats not 0 and its positive (like 10) to get rid of it. I'm not sure how you would tell it to 'skip' grub, I'm not that good in this stuff and I think this Timeout=0 used to work on previous Grub.

Read grub.cfg, comments in configuration files are always usefull :D I'm not in mood to read it so I'll let you do it. It's located in /boot/grub/

To find stuff you're searching for faster, use Ctrl + F and type keywords :)

---

