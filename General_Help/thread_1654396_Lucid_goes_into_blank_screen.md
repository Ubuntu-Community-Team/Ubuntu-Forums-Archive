---
title: "Lucid goes into blank screen"
date: 2010-12-28
forum: General Help
---

### Post by serlex on 2010-12-28
Hi,

I have a Samsung laptop, running Windows 7 and Ubuntu Lucid

Both operating systems were working fine, until Ubuntu no longer began booting properly.

After grub, the screen goes blank (black).

I don't remember installing before this happened.

I can get into recovery mode and get networking via cable

I've tried apt-get update/upgrade

I've tried removing 'quite splash and using nomodeset 

Laptop is using nvidia (with cuba) graphics card

---

### Post by serlex on 2010-12-28
Anyone?

I've tried the following in Recovery Mode

```

dpkg-reconfigure gdm
dpkg-reconfigure xserver-xorg
dpkg-reconfigure -phigh xserver-org

```

All three just goes to a new line

:confused:

---

### Post by serlex on 2010-12-28
removed xorg and reinstalled

It looks slightly better now. It boots, goes into tty1 (login screen)

When I type 'startx', says 'No screens found'

---

### Post by serlex on 2010-12-28
Removed nvidia completely 'apt-get remove --purge nvidia*'

Restarted, gets stuck at 'Checking battery state'

Got into tty1 CTRL + ALT F1 and run startx

Got GUI, but can't switch to normal user

any ideas?

Should I install later nvidia driver from their website?

---

### Post by serlex on 2010-12-29
don't mess around like I did above. I had some dodgy Android phone rules in /etc/udev/rules.d. Removed them and back on!

---

